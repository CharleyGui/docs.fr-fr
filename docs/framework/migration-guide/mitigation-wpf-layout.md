---
title: 'Atténuation : disposition WPF'
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
ms.openlocfilehash: 7a074698fd203d0c5f9b799bfee8a6a9cb40800e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457781"
---
# <a name="mitigation-wpf-layout"></a>Atténuation : disposition WPF
La disposition des contrôles WPF peut varier légèrement.  
  
## <a name="impact"></a>Impact  
 Résultat de cette modification :  
  
- La largeur ou la hauteur d'éléments peut croître ou diminuer d'un pixel au plus.  
  
- La position d'un objet peut se déplacer d'un pixel au plus.  
  
- Les éléments centrés peuvent être décalés verticalement ou horizontalement d'un pixel au plus.  
  
 Par défaut, cette nouvelle disposition est activée uniquement pour les applications qui ciblent le .NET. Framework 4.6.  
  
## <a name="mitigation"></a>Limitation des risques  
 Dans la mesure où cette modification tend à éliminer le découpage droit ou inférieur des contrôles WPF dont le PPP est élevé, les applications qui ciblent les versions antérieures du .NET Framework, mais qui s'exécutent sur le .NET Framework 4.6, peuvent choisir ce nouveau comportement en ajoutant la ligne suivante à la section `<runtime>` du fichier app.config :  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 Les applications qui ciblent le .NET Framework 4.6, mais veulent que les contrôles WPF soient rendus à l'aide de l'algorithme de disposition précédent peuvent y parvenir en ajoutant la ligne suivante à la section `<runtime>` du fichier app.config :  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a>Voir aussi

- [Compatibilité des applications](application-compatibility.md)
