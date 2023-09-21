---
description: Vous devez séparer la logique de l’interface utilisateur de votre lecteur du processus qui gère les clics publicitaires. Pour ce faire, vous pouvez mettre en oeuvre plusieurs fragments pour une activité.
title: Séparez le processus de publicité cliquable
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# Séparez le processus de publicité cliquable {#separate-the-clickable-ad-process}

Vous devez séparer la logique de l’interface utilisateur de votre lecteur du processus qui gère les clics publicitaires. Pour ce faire, vous pouvez mettre en oeuvre plusieurs fragments pour une activité.

1. Mettez en oeuvre un fragment pour contenir le `MediaPlayer`.

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

1. Mettez en oeuvre un autre fragment pour afficher un élément d’interface utilisateur qui indique qu’une publicité peut être cliquée, surveiller cet élément d’interface utilisateur et communiquer les clics de l’utilisateur au fragment qui contient le `MediaPlayer`.

   Ce fragment doit déclarer une interface pour la communication du fragment. Le fragment capture l’implémentation de l’interface au cours de sa `onAttach()` méthode de cycle de vie et peut appeler les méthodes d’interface pour communiquer avec l’activité.

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
