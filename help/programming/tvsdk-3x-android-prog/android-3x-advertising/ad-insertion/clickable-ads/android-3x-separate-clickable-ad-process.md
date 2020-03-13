---
description: Vous devez séparer la logique de l’interface utilisateur de votre lecteur du processus qui gère les clics publicitaires. Pour ce faire, vous pouvez implémenter plusieurs fragments pour un  .
seo-description: Vous devez séparer la logique de l’interface utilisateur de votre lecteur du processus qui gère les clics publicitaires. Pour ce faire, vous pouvez implémenter plusieurs fragments pour un  .
seo-title: Séparer le processus publicitaire cliquable
title: Séparer le processus publicitaire cliquable
uuid: a5254ac5-3005-483e-935e-acbbef03df0e
translation-type: tm+mt
source-git-commit: bc35da8b258056809ceaf18e33bed631047bc81b

---


# Séparer le processus publicitaire cliquable {#separate-the-clickable-ad-process}

Vous devez séparer la logique de l’interface utilisateur de votre lecteur du processus qui gère les clics publicitaires. Pour ce faire, vous pouvez implémenter plusieurs fragments pour un  .

1. Implémentez un fragment pour le contenir `MediaPlayer`.

   Ce fragment doit appeler `notifyClick()` et sera responsable de la lecture vidéo.

   ```java
   public class PlayerFragment extends SherlockFragment { 
       ... 
       public void notifyAdClick () { 
           _mediaPlayer.notifyClick(); 
       } 
       ... 
   } 
   ```

1. Implémentez un autre fragment pour afficher un élément de l’interface utilisateur qui indique qu’une publicité peut être cliquée, surveillez cet élément de l’interface utilisateur et communiquez les clics de l’utilisateur au fragment qui contient le `MediaPlayer`.

   Ce fragment doit déclarer une interface pour la communication des fragments. Le fragment capture l’implémentation de l’interface au cours de sa méthode de `onAttach()` cycle de vie et peut appeler les méthodes de l’interface pour communiquer avec le  .

   ```java
   public class PlayerClickableAdFragment extends SherlockFragment { 
       private ViewGroup viewGroup; 
       private Button button; 
       OnAdUserInteraction callback; 
       @Override 
       public View onCreateView(LayoutInflater inflater,  
                                ViewGroup container,  
                                Bundle savedInstanceState) { 
           // the custom fragment is defined by a custom button 
           viewGroup = (ViewGroup) inflater.inflate(R.layout.fragment_player_clickable_ad,  
                                                    container, false); 
           button = (Button) viewGroup.findViewById(R.id.clickButton); 
   
           // register a click listener to detect user interaction 
           button.setOnClickListener(new View.OnClickListener() { 
               @Override 
               public void onClick(View v) { 
                   // send the event back to the activity 
                   callback.onAdClick(); 
               } 
           }); 
           viewGroup.setVisibility(View.INVISIBLE); 
           return viewGroup; 
       } 
   
       public void hide() { 
           viewGroup.setVisibility(View.INVISIBLE); 
       } 
   
       public void show() { 
           viewGroup.setVisibility(View.VISIBLE);     
       } 
   
       @Override 
       public void onAttach(Activity activity) { 
           super.onAttach(activity); 
           // attaches the interface implementation 
           // if the container activity does not implement the methods  
           // from the interface an exception will be thrown 
           try { 
               callback = (OnAdUserInteraction) activity; 
           } catch (ClassCastException e) { 
               throw new ClassCastException(activity.toString() 
                   + " must implement OnAdUserInteraction"); 
           }     
       } 
   
       // user defined interface that allows fragment communication 
       // must be implemented by the container activity 
       public interface OnAdUserInteraction { 
           public void onAdClick(); 
       } 
   } 
   ```
