---
description: Cette section traite de la grammaire de l'entrée de configuration, met l'accent sur les options d'entrée valides et non valides et explique comment les champs facultatifs omis sont interprétés.
seo-description: Cette section traite de la grammaire de l'entrée de configuration, met l'accent sur les options d'entrée valides et non valides et explique comment les champs facultatifs omis sont interprétés.
seo-title: Grammaire RBOP
title: Grammaire RBOP
uuid: d9064e39-593a-4767-b835-287640b4c94a
translation-type: tm+mt
source-git-commit: e60d285b9e30cdd19728e3029ecda995cd100ac9

---


# Grammaire RBOP {#rbop-grammar}

Cette section traite de la grammaire de l&#39;entrée de configuration, met l&#39;accent sur les options d&#39;entrée valides et non valides et explique comment les champs facultatifs omis sont interprétés.

La grammaire de la protection de sortie basée sur la résolution est définie comme une séquence de règles, où chaque règle peut avoir plusieurs formulaires valides :

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

1. L’ordre des paires définies dans les objets n’est pas fixe ; par conséquent, toute permutation des paires est valide.

   Par exemple, si nous avons défini un objet de ce type :

   ```
   {  
     "foo": <Foo>,  
     "bar":<Bar>,  
     "baz":<Baz>  
   }
   ```

   ensuite, la structure suivante serait également considérée comme valide : =

   ```
   {  
     "baz":<Baz>,  
     "foo":<Foo>,  
     "bar":<Bar> 
   }
   ```

1. Pour chaque paire d’un objet, on suppose qu’il n’existe qu’une seule instance de cette paire dans une instance donnée d’un objet donné.

   Par exemple, si nous avons défini un objet de ce type :

   ```
   {  
     "foo": <Foo>,  
     "bar":<Bar>,  
     "baz":<Baz>  
   }
   ```

   l’instance suivante serait alors non valide, car il existe deux `foo` paires au sein du même objet :

   ```
   { 
     "foo":<Foo>,  
     "bar":<Bar>,  
     "baz":<Baz>,  
   } 
   ```

   De même, il comporte deux objets tels que :

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

1. Pour les définitions où une ou plusieurs chaînes peuvent être sélectionnées, traitez les chaînes comme un ensemble, dans lequel les entrées de duplicata sont traitées comme une seule entrée. Par exemple, `["foo", "bar", "foo", "baz"]` est équivalent à `["foo", "bar", "baz"]`

1. Pour définir des nombres, un espace est utilisé entre les règles (p. ex. `Digit Digits`), mais aucun espace ne doit être utilisé lors de l’application de la règle.

   Par exemple, si nous exprimons le nombre *cent vingt-trois* par règle NonZeroInteger, il doit être exprimé comme `123` plutôt que `1 2 3`comme, même si la règle contient un espace entre NonZeroDigit et Chiffres.

1. Certaines règles autorisent plusieurs formulaires. Dans ce cas, les différents formulaires sont séparés par le `'|'` caractère.

   Par exemple, cette règle :

   ```
   Foo ::= "A" | "B" | "C"
   ```

   signifie qu’une instance de `Foo` peut être remplacée par &quot;A&quot;, &quot;B&quot; ou &quot;C&quot;. Cela ne doit pas être confondu avec un formulaire qui s’étend sur plusieurs lignes ; c&#39;est une fonctionnalité qui permet de rendre les formulaires plus longs plus lisibles.

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

## Sémantique : Configurations légales mais non valides {#section_709BE240FF0041D4A1B0A0A7544E4966}

La rubrique Configuration *de la protection* d’extraction d’échantillon présentait une configuration valide ainsi que sa signification sémantique. La section précédente de *cette* rubrique présentait les règles de grammaire pour les configurations. Bien que la grammaire aide à assurer l&#39;exactitude syntaxique, il existe des configurations syntaxiquement légales qui ne sont pas sémantiquement correctes (c&#39;est-à-dire qu&#39;elles ne sont pas logiques). Cette section présente des configurations *syntaxiquement* légales, mais *sémantiquement* incorrectes. N&#39;oubliez pas que les exemples de cette section ont été réduits à la structure minimale nécessaire pour illustrer le scénario en discussion.

* Il n&#39;est pas valide de définir plusieurs contraintes de pixels avec le même nombre de pixels.

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
