---
ms.openlocfilehash: f78d15338aa49de5b729aca12964924a0df00ec6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614548"
---
### <a name="improved-accessibility-for-some-net-sdk-tools"></a>Amélioration de l’accessibilité pour certains outils du SDK .NET

#### <a name="details"></a>Détails

Dans le kit .NET Framework SDK 4.7.1, les outils SvcConfigEditor.exe et SvcTraceViewer.exe ont été améliorés en corrigeant différents problèmes d’accessibilité. La plupart étaient des petits problèmes comme un nom non défini ou certains modèles d’automatisation de l’interface utilisateur non implémentés correctement. Si de nombreux utilisateurs n’ont pas conscience de ces valeurs incorrectes, les clients qui utilisent des technologies d’assistance comme les lecteurs d’écran trouveront ces outils du kit de développement logiciel (SDK) plus accessibles. Il est évident que ces correctifs changent certains comportements précédents, comme l’ordre de focus clavier. Pour obtenir tous les correctifs liés à l’accessibilité dans ces outils, vous pouvez ajouter ce qui suit à votre fichier app.config :

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false"/>
</runtime>
```

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4.7.1       |
| Type    | Reciblage |
