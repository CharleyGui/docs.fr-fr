---
title: 'Atténuation : gestion de versions de produit'
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8811fd916afcb39c466b8c9a60f7c7ed2a62ea8
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301436"
---
# <a name="mitigation-product-versioning"></a>Atténuation : gestion de versions de produit
Dans .NET Framework 4.6 et ultérieur, la gestion des versions de produit a changé par rapport aux versions précédentes du .NET Framework (.NET Framework 4, 4.5, 4.5.1 et 4.5.2).  
  
## <a name="product-versioning-changes"></a>Modifications de la gestion de versions de produit  
 Voici le détail des modifications :  
  
- La valeur de l’entrée `Version` dans la clé `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` a été remplacée par `4.6.`*xxxxx* pour le .NET Framework 4.6 et ses versions intermédiaires, et par `4.7.`*xxxxx* pour le .NET Framework 4.7. Dans le .NET Framework 4.5, 4.5.1 et 4.5.2, elle était au format `4.5.`*xxxxx*.  
  
- La gestion des versions des fichiers et des produits pour les fichiers du .NET Framework est passé de l’ancien schéma `4.0.30319.x` au schéma `4.6.X.0` pour le .NET Framework 4.6 et ses versions intermédiaires, et au schéma `4.7.X.0` pour le .NET Framework 4.7 et ses versions intermédiaires. Pour voir ces nouvelles valeurs, cliquez avec le bouton droit sur un fichier, puis affichez ses **Propriétés**.  
  
- Les attributs <xref:System.Reflection.AssemblyFileVersionAttribute> et <xref:System.Reflection.AssemblyInformationalVersionAttribute> pour les assemblys managés ont des valeurs <xref:System.Version> au format `4.6.X.0` pour le .NET Framework 4.6 et ses versions intermédiaires, et `4.7.X.0` pour le Framework .NET 4.7.  
  
- Dans .NET Framework 4.6, 4.6.1, 4.6.2 et 4.7, la propriété <xref:System.Environment.Version%2A?displayProperty=nameWithType> retourne la chaîne de version fixe `4.0.30319.42000`. Dans le .NET Framework 4, 4.5, 4.5.1 et 4.5.2, elle retourne les chaînes de version au format `4.0.30319.xxxxx` (par exemple, « 4.0.30319.18010 »). Notez que nous ne recommandons pas que le code d'application prenne de nouvelles dépendances sur la propriété <xref:System.Environment.Version%2A?displayProperty=nameWithType>.  
  
### <a name="handling-the-product-versioning-changes"></a>Gestion des modifications du contrôle de version de produit  
 En général, les applications doivent s'appuyer sur les techniques recommandées pour la détection d'éléments tels que la version de runtime du .NET Framework et le répertoire d'installation :  
  
- Pour détecter la version du runtime du .NET Framework, consultez [Guide pratique pour déterminer les versions du .NET Framework installées](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).  
  
- Pour déterminer le chemin d'installation du .NET Framework, utilisez la valeur de l'entrée `InstallPath` dans la clé `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`.  
  
    > [!IMPORTANT]
    >  Le nom de la sous-clé est `NET Framework Setup`, et non `.NET Framework Setup`.  
  
- Pour déterminer le chemin d'accès du répertoire du Common Language Runtime du .NET Framework, appelez la méthode <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType>.  
  
- Pour obtenir la version du CLR, appelez la méthode <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType>.   Pour .NET Framework 4 et ses versions intermédiaires (.NET Framework 4.5, 4.5.1, 4.5.2 ainsi que .NET Framework 4.6, 4.6.1, 4.6.2 et 4.7), elle retourne la chaîne `v4.0.30319`.  
  
## <a name="see-also"></a>Voir aussi

- [Modifications du runtime](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
