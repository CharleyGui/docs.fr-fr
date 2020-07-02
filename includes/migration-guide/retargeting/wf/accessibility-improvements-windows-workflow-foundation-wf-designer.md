---
ms.openlocfilehash: d420be76645fc71ac922542fa49f799a473e9a83
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614557"
---
### <a name="accessibility-improvements-in-windows-workflow-foundation-wf-workflow-designer"></a>Améliorations de l’accessibilité dans le Concepteur de flux de travail Windows Workflow Foundation (WF)

#### <a name="details"></a>Détails

Le Concepteur de flux de travail Windows Workflow Foundation (WF) améliore son fonctionnement avec les technologies d’accessibilité. Ces améliorations incluent notamment les changements suivants :

- L’ordre de tabulation est modifié pour passer de gauche à droite et de haut en bas dans certains contrôles :
- La fenêtre d’initialisation de la corrélation pour définir les données de corrélation pour l’activité <xref:System.ServiceModel.Activities.InitializeCorrelation>
- La fenêtre de définition du contenu pour les activités <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply> et <xref:System.ServiceModel.Activities.ReceiveReply>
- D’autres fonctions sont disponibles par le biais du clavier :
- Quand vous modifiez les propriétés d’une activité, les groupes de propriétés peuvent être réduits à l’aide du clavier la première fois qu’ils ont le focus.
- Des icônes d’avertissement sont désormais accessibles à l’aide du clavier.
- Le bouton Plus de propriétés de la fenêtre Propriétés est désormais accessible à l’aide du clavier.
- Les utilisateurs du clavier peuvent désormais accéder aux éléments d’en-tête dans les volets Arguments et Variables du Concepteur de flux de travail.
- Une meilleure visibilité des éléments ayant le focus, par exemple dans les cas suivants :
- Ajout de lignes dans des grilles de données utilisées par le Concepteur de flux de travail et les concepteurs d’activités.
- Déplacement par tabulation dans les champs des activités <xref:System.ServiceModel.Activities.ReceiveReply> et <xref:System.ServiceModel.Activities.SendReply>.
- Définition de valeurs par défaut pour les variables ou les arguments
- Les lecteurs d’écran peuvent désormais reconnaître correctement :
- Les points d’arrêt définis dans le Concepteur de flux de travail.
- Les activités <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision> et <xref:System.ServiceModel.Activities.CorrelationScope>.
- Le contenu de l’activité <xref:System.ServiceModel.Activities.Receive>.
- Le type cible pour l’activité <xref:System.Activities.Statements.InvokeMethod>.
- La zone de liste déroulante Exception et la section Finally de l’activité <xref:System.Activities.Statements.TryCatch>.
- La zone de liste déroulante Type de message, le séparateur dans la fenêtre Ajouter des initialiseurs de corrélation, la fenêtre de définition du contenu et la fenêtre Définition de CorrelatesOn dans les activités de messagerie (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply> et <xref:System.ServiceModel.Activities.ReceiveReply>).
- Transitions d’ordinateur d’état et destination des transitions.
- Annotations et connecteurs sur les activités <xref:System.Activities.Statements.FlowDecision>.
- Les menus contextuels (accessibles en cliquant avec le bouton droit) pour les activités.
- Les éditeurs de valeurs de propriété, le bouton Effacer la recherche, les boutons a catégorie par et boutons de tri Par catégorie et Ordre alphabétique et la boîte de dialogue Éditeur d’expressions dans la grille des propriétés.
- Le pourcentage de zoom dans le Concepteur de flux de travail.
- Le séparateur dans les activités <xref:System.Activities.Statements.Parallel> et <xref:System.Activities.Statements.Pick>.
- L’activité <xref:System.Activities.Statements.InvokeDelegate>.
- La fenêtre Sélectionner les types pour les activités de dictionnaire (`Microsoft.Activities.AddToDictionary&lt;TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary&lt;TKey,TValue>`, etc.).
- La fenêtre Rechercher et sélectionner un type .NET.
- Les barres de navigation dans le Concepteur de flux de travail.
- Les utilisateurs qui choisissent des thèmes à contraste élevé verront de nombreuses améliorations de la visibilité du Concepteur de flux de travail et de ses contrôles, comme de meilleurs rapports de contraste entre les éléments et des zones de sélection plus visibles utilisées pour les éléments ayant le focus.

#### <a name="suggestion"></a>Suggestion

Si vous avez une application avec un Concepteur de flux de travail réhébergé, effectuez l’une des actions suivantes pour qu’elle bénéficie de ces changements :

- Recompilez votre application pour cibler .NET Framework 4.7.1. Ces changements de l’accessibilité sont activés par défaut.
- Si votre application cible .NET Framework 4.7 ou une version antérieure mais qu’elle s’exécute sur .NET Framework 4.7.1, vous pouvez refuser ces comportements d’accessibilité hérités en ajoutant le [commutateur AppContext](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivant à la section `<runtime>` du fichier app.config et en lui affectant la valeur `false`, comme indiqué dans l’exemple suivant.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
  </startup>
  <runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
  </runtime>
</configuration>
```

Si votre application cible .NET Framework 4.7.1 ou une version ultérieure et que vous souhaitez conserver le comportement d’accessibilité hérité, choisissez d’utiliser les fonctionnalités d’accessibilité héritées en affectant explicitement à ce commutateur AppContext la valeur `true`.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4.7.1       |
| Type    | Reciblage |
