---
title: MEF pour .NET pour les applications du Windows Store
ms.date: 03/30/2017
ms.assetid: 7667770e-d163-4ad6-a303-085cf73db2f2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b2b62e6fea6da46e6307b35dd1c3372420dced80
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648514"
---
# <a name="mef-for-net-for-windows-store-apps"></a>MEF pour .NET pour les applications du Windows Store
<xref:System.Composition?displayProperty=nameWithType> et ses espaces de noms enfants contiennent des types pour développer des applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] extensibles avec Managed Extensibility Framework (MEF). Ces espaces de noms font partie du sous-ensemble [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] du système d’exploitation [!INCLUDE[win8](../../../includes/win8-md.md)].  
  
 Ces espaces de noms ne font pas partie de la bibliothèque de classes de base distribuée avec le .NET Framework. Pour installer ces espaces de noms, ouvrez votre projet dans Visual Studio, sélectionnez **Gérer les packages NuGet** dans le menu **Projet**, puis recherchez le package Microsoft.Composition en ligne.  
  
- <xref:System.Composition?displayProperty=nameWithType> fournit des classes qui constituent le MEF de base pour les applications [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)].  
  
- <xref:System.Composition.Convention?displayProperty=nameWithType> fournit des types qui prennent en charge l’utilisation de MEF avec un modèle de configuration basée sur une convention.  
  
- <xref:System.Composition.Hosting?displayProperty=nameWithType> fournit des types MEF qui sont utiles aux développeurs d’applications hôtes.  
  
- <xref:System.Composition.Hosting.Core?displayProperty=nameWithType> fournit des types MEF utilisés en interne par le moteur de composition.  
  
 Pour obtenir plus d’informations sur [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] et une liste des espaces de noms et des types qu’il contient, consultez [Vue d’ensemble de .NET pour les applications Windows Store](https://go.microsoft.com/fwlink/p/?LinkID=238312) dans le Centre de développement Windows.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de .NET pour les applications Windows Store](https://go.microsoft.com/fwlink/p/?LinkID=238312)
- [.NET pour les applications du Windows Store : API prises en charge](https://go.microsoft.com/fwlink/p/?LinkID=247912)
- [Managed Extensibility Framework (MEF)](../../../docs/framework/mef/index.md)
