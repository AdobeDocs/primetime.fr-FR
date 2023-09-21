---
description: Cette section décrit la grammaire de l’entrée de configuration, met l’accent sur les options de saisie valides et non valides et explique comment les champs facultatifs omis sont interprétés.
title: RBOP Grammar
source-git-commit: 02ebc3548a254b2a6554f1ab34afbb3ea5f09bb8
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# RBOP Grammar {#rbop-grammar}

Cette section décrit la grammaire de l’entrée de configuration, met l’accent sur les options de saisie valides et non valides et explique comment les champs facultatifs omis sont interprétés.

La grammaire de protection de sortie basée sur la résolution est définie comme une séquence de règles, où chaque règle peut avoir plusieurs formulaires valides :

```
Rule ::=       
 
    Form 
     
AnotherRule ::=     
 
    DifferentForm 
```

## Application des règles de grammaire {#section_A7216BD585FF4EB88737B643B36C2781}

>[!NOTE]
>
>Pour améliorer la lisibilité de la grammaire, les propriétés suivantes ne sont pas reflétées dans la grammaire mais conservent la valeur true :

1. L’ordre des paires défini dans les objets n’est pas fixe. Par conséquent, toute permutation des paires est valide.

   Par exemple, si nous avons défini un objet comme suit :

   ```
   {  
     "foo": <Foo>,  
     "bar":<Bar>,  
     "baz":<Baz>  
   }
   ```

   la structure suivante serait également considérée comme valide : =

   ```
   {  
     "baz":<Baz>,  
     "foo":<Foo>,  
     "bar":<Bar> 
   }
   ```

1. Pour chaque paire au sein d’un objet, on suppose qu’il n’existe qu’une seule instance de cette paire dans une instance donnée d’un objet donné.

   Par exemple, si nous avons défini un objet comme suit :

   ```
   {  
     "foo": <Foo>,  
     "bar":<Bar>,  
     "baz":<Baz>  
   }
   ```

   l’instance suivante serait alors invalide, car il existe deux `foo` paires au sein du même objet :

   ```
   { 
     "foo":<Foo>,  
     "bar":<Bar>,  
     "baz":<Baz>,  
   } 
   ```

   De même, deux objets tels que :

   ```
   {  
     "foo": <Foo>,  
     "bar":<Bar>,  
     "baz":<Baz>  
   }
   ```

   et :

   ```
   {  
     "baz":<Baz>,  
     "foo":<Foo>,  
     "bar":<Bar> 
   }
   ```

   est valide, puisqu’il s’agit d’instances indépendantes du même objet.

1. Pour les définitions dans lesquelles une ou plusieurs chaînes peuvent être sélectionnées, traitez les chaînes comme un ensemble, dans lequel les entrées en double sont traitées comme une seule entrée. Par exemple : `["foo", "bar", "foo", "baz"]` équivaut à `["foo", "bar", "baz"]`

1. Pour définir des nombres, un espace est utilisé entre les règles (par exemple, `Digit Digits`), mais aucun espace de ce type ne doit être utilisé lors de l’application de la règle.

   Par exemple, si nous exprimons le nombre *cent vingt trois* Selon la règle NonZeroInteger , elle doit être exprimée comme `123` plutôt que `1 2 3`, même si la règle contient un espace entre NonZeroDigit et Digits.

1. Certaines des règles autorisent plusieurs formulaires. Dans ce cas, les différents formulaires sont séparés par le `'|'` caractère.

   Par exemple, cette règle :

   ```
   Foo ::= "A" | "B" | "C"
   ```

   signifie qu’une instance de `Foo` peut être remplacé par &quot;A&quot;, &quot;B&quot; ou &quot;C&quot;. Cela ne doit pas être confondu avec un formulaire qui s’étend sur plusieurs lignes ; c’est une fonctionnalité qui rend les formulaires plus longs plus lisibles.

## La Grammar {#section_52189FD66B1A46BA9F8FDDE1D7C8E8E8}

```
PixelBasedOPConfig ::= 
      {} 
    | { "maxPixel": NonNegativeInteger } 
    | { "pixelConstraints": PixelConstraintsSeq } 
    | { "pixelConstraints": PixelConstraintsSeq, 
        "maxPixel": NonNegativeInteger } 
 
PixelConstraintsSeq ::= 
      [] 
    | [ PixelConstraints ] 
 
PixelConstraints ::= 
      PixelConstraint 
    | PixelConstraint, PixelConstraints 
 
PixelConstraint ::= 
      { "pixelCount": NonNegativeInteger } 
    | { "pixelCount": NonNegativeInteger, 
        "digital": DigitalOutputRestrictionsSeq } 
    | { "pixelCount": NonNegativeInteger, 
        "analog": AnalogOutputRestriction } 
    | { "pixelCount": NonNegativeInteger, 
        "ota": OTAOutputRestriction } 
    | { "pixelCount": NonNegativeInteger, 
        "digital": DigitalOutputRestrictionsSeq, 
        "analog": AnalogOutputRestriction } 
    | { "pixelCount": NonNegativeInteger, 
        "digital": DigitalOutputRestrictionsSeq, 
         "ota": OTAOutputRestriction } 
    | { "pixelCount": NonNegativeInteger, 
        "analog": AnalogOutputRestriction, 
        "ota": OTAOutputRestriction } 
    | { "pixelCount": NonNegativeInteger, 
        "digital": DigitalOutputRestrictionsSeq, 
        "analog": AnalogOutputRestriction, 
        "ota": OTAOutputRestriction } 
 
DigitalOutputRestrictionsSeq ::= 
      [] 
    | [ DigitalOutputRestrictions ] 
 
DigitalRestrictions ::= 
      DigitalRestriction 
    | DigitalRestriction, DigitalRestrictions 
 
DigitalRestriction ::= 
      { "output": DigitalOutputOption } 
    | { "output": DigitalOutputOption, "hdcp": HDCP } 
 
DigitalOutputOption ::= 
      "NO_PROTECTION" 
    | "USE_IF_AVAILABLE" 
    | "REQUIRED" 
    | "NO_PLAYBACK" 
 
HDCP ::= 
    { "major": PositiveInteger, "minor": NonNegativeInteger } 
 
AnalogOutputRestriction ::= 
    { "output": AnalogOutputOption } 
 
AnalogOutputOption ::= 
      "NO_PROTECTION" 
    | "USE_IF_AVAILABLE" 
    | "USE_IF_AVAILABLE_ACP" 
    | "USE_IF_AVAILABLE_CGMSA" 
    | "REQUIRED" 
    | "REQUIRED_ACP" 
    | "REQUIRED_CGMSA" 
    | "NO_PLAYBACK" 
 
OTAOutputRestriction ::= 
    { "whitelist": OTAWhitelistSeq } 
 
OTAWhitelistSeq ::= 
      [] 
    | [ OTAWhitelist ] 
 
OTAWhitelist ::= 
      OTAConnectionType 
    | OTAConnectionType, OTAWhitelist 
 
OTAConnectionType ::= 
      "MIRACAST" 
    | "AIRPLAY" 
    | "WIDI" 
    | "DLNA" 
 
NonNegativeInteger ::= 
      Digit 
    | NonZeroDigit Digits 
 
PositiveInteger ::= 
      NonZeroDigit 
    | NonZeroDigit Digits 
 
Digits ::= 
      Digit 
    | Digit Digits 
 
Digit ::= 
      0 
    | NonZeroDigit

NonZeroDigit ::= 
      1 
    | 2 
    | 3 
    | 4 
    | 5 
    | 6 
    | 7 
    | 8 
    | 9
```

## Sémantique : configurations juridiques mais non valides {#section_709BE240FF0041D4A1B0A0A7544E4966}

La variable *Exemple de configuration de protection de sortie* La rubrique présentait une configuration valide ainsi que sa signification sémantique. La section précédente de *this* La rubrique présentait les règles de grammaire pour les configurations. Bien que la grammaire permette d&#39;assurer l&#39;exactitude syntaxique, il existe des configurations syntaxiquement légales qui ne sont pas sémantiquement correctes (c&#39;est-à-dire qu&#39;elles ne sont pas logiques). Cette section présente les configurations qui *syntaxique* légal, mais *sémantique* incorrect. Gardez à l’esprit que les exemples de cette section ont été réduits à la structure minimale nécessaire pour illustrer le scénario en cours de discussion.

* Il n’est pas valide de définir des contraintes de plusieurs pixels avec le même nombre de pixels.

  ```
  {  
    "pixelConstraints":  
      [  
        { "pixelCount": 720 }  
      ]  
   }  
  ```

* Le nombre de pixels ne doit pas dépasser la résolution maximale spécifiée.

  ```
  { 
    "maxPixel": 720, 
    "pixelConstraints": 
      [ 
        {"pixelCount": 1080} 
      ] 
  } 
  ```
