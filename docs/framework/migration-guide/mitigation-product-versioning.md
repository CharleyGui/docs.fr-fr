---
title: 'Atténuation : Gestion de versions de produit'
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
ms.openlocfilehash: 64a68d2b79a0a3ccdd806949ffd6cb3760974390
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457826"
---
# <a name="mitigation-product-versioning"></a>Atténuation : Gestion de versions de produit

Dans .NET Framework 4.6 et ultérieur, la gestion des versions de produit a changé par rapport aux versions précédentes du .NET Framework (.NET Framework 4, 4.5, 4.5.1 et 4.5.2).

## <a name="product-versioning-changes"></a>Modifications de la gestion de versions de produit

Voici le détail des modifications :

- La valeur de l’entrée `Version` dans la clé `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` a été remplacée par `4.6.`*xxxxx* pour le .NET Framework 4.6 et ses versions intermédiaires, et par `4.7.`*xxxxx* pour le .NET Framework 4.7. Dans le .NET Framework 4.5, 4.5.1 et 4.5.2, elle était au format `4.5.`*xxxxx*.

- La gestion des versions des fichiers et des produits pour les fichiers du .NET Framework est passé de l’ancien schéma `4.0.30319.x` au schéma `4.6.X.0` pour le .NET Framework 4.6 et ses versions intermédiaires, et au schéma `4.7.X.0` pour le .NET Framework 4.7 et ses versions intermédiaires. Vous pouvez voir ces nouvelles valeurs lorsque vous affichez les **propriétés** du fichier après avoir cliqué sur un fichier.

- Les attributs <xref:System.Reflection.AssemblyFileVersionAttribute> et <xref:System.Reflection.AssemblyInformationalVersionAttribute> pour les assemblys managés ont des valeurs <xref:System.Version> au format `4.6.X.0` pour le .NET Framework 4.6 et ses versions intermédiaires, et `4.7.X.0` pour le Framework .NET 4.7.

- À compter de .NET Framework 4.6, la propriété <xref:System.Environment.Version%2A?displayProperty=nameWithType> retourne la chaîne de version fixe `4.0.30319.42000`. Dans .NET Framework 4, 4.5, 4.5.1 et 4.5.2, elle retourne les chaînes de version au format `4.0.30319.xxxxx`, où `xxxxx` est inférieur à 42000 (par exemple « 4.0.30319.18010 »). Notez que nous ne recommandons pas que le code d'application prenne de nouvelles dépendances sur la propriété <xref:System.Environment.Version%2A?displayProperty=nameWithType>.

### <a name="handling-the-product-versioning-changes"></a>Gestion des modifications de la gestion de versions de produit

En général, les applications doivent s'appuyer sur les techniques recommandées pour la détection d'éléments tels que la version de runtime du .NET Framework et le répertoire d'installation :

- Pour détecter la version de runtime du .NET Framework, consultez [Guide pratique pour déterminer les versions .NET Framework installées](how-to-determine-which-versions-are-installed.md).

- Pour déterminer le chemin d'installation du .NET Framework, utilisez la valeur de l'entrée `InstallPath` dans la clé `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`.

  > [!IMPORTANT]
  > Le nom de la sous-clé est `NET Framework Setup`, et non `.NET Framework Setup`.

- Pour déterminer le chemin d'accès du répertoire du Common Language Runtime du .NET Framework, appelez la méthode <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType>.

- Pour obtenir la version du CLR, appelez la méthode <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType>.   Pour .NET Framework 4 et ses versions intermédiaires (.NET Framework 4.5, 4.5.1, 4.5.2 ainsi que .NET Framework 4.6, 4.6.1, 4.6.2 et 4.7), elle retourne la chaîne `v4.0.30319`.

## <a name="see-also"></a>Voir aussi

- [Compatibilité des applications](application-compatibility.md)
