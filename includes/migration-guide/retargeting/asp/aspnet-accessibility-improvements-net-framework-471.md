---
ms.openlocfilehash: 418bcdca1e9a325894891d7b0e080ce035e2d1b4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614459"
---
### <a name="aspnet-accessibility-improvements-in-net-framework-471"></a>Améliorations de l’accessibilité ASP.NET dans .NET Framework 4.7.1

#### <a name="details"></a>Détails

À compter de .NET Framework 4.7.1, ASP.NET a amélioré le fonctionnement des contrôles web ASP.NET avec la technologie d’accessibilité de Visual Studio pour une meilleure prise en charge des clients ASP.NET.  Citons notamment les changements suivants :

- Changements visant à implémenter les modèles d’accessibilité de l’interface utilisateur manquants dans les contrôles, comme la boîte de dialogue Ajouter un champ de l’Assistant de la vue Détails ou la boîte de dialogue Configurer ListView de l’Assistant ListView.
- Changements visant à améliorer l’affichage en mode de contraste élevé, comme l’éditeur de champs du pagineur de données.
- Changements visant à améliorer les expériences de navigation au clavier pour les contrôles, comme la boîte de dialogue Champs de l’Assistant Modifier les champs pager du contrôle DataPager, la boîte de dialogue Configurer ObjectContext ou la boîte de dialogue Configurer la sélection de données de l’Assistant Configurer la source de données.

#### <a name="suggestion"></a>Suggestion

**Comment accepter ou refuser ces changements** Pour que le concepteur Visual Studio tire parti de ces changements, il doit s’exécuter sur .NET Framework 4.7.1 ou ultérieur. Pour que l’application web tire parti de ces changements, procédez de l’une des manières suivantes :

- Installez Visual Studio 2017 15.3 ou une version ultérieure, qui prend en charge les nouvelles fonctionnalités d’accessibilité avec le commutateur AppContext suivant par défaut.
- Refusez les comportements d’accessibilité hérités en ajoutant le commutateur AppContext `Switch.UseLegacyAccessibilityFeatures` à la section `<runtime>` du fichier devenv.exe.config et en lui affectant la valeur `false`, comme indiqué dans l’exemple suivant.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
<runtime>
...
<!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false'  -->
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
...
</runtime>
</configuration>
```

Si votre application cible .NET Framework 4.7.1 ou une version ultérieure et que vous souhaitez conserver le comportement d’accessibilité hérité, choisissez d’utiliser les fonctionnalités d’accessibilité héritées en affectant explicitement à ce commutateur AppContext la valeur `true`.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4.7.1       |
| Type    | Reciblage |
