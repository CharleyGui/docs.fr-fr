---
title: Réflexion dans le .NET Framework pour les applications Windows Store
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- reflection, Windows Store apps
- .NET for Windows Store apps, TypeInfo class
ms.assetid: 0d07090c-9b47-4ecc-81d1-29d539603c9b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b5503d8a474d7f19348b9342bc02e216bd987223
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66378608"
---
# <a name="reflection-in-the-net-framework-for-windows-store-apps"></a>Réflexion dans le .NET Framework pour les applications Windows Store
À compter de .NET Framework 4.5, le .NET Framework fournit un ensemble de types et membres de réflexion à utiliser dans les applications du [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]. Ces types et membres sont disponibles dans le .NET Framework complet et dans [.NET pour les applications du Windows Store](https://go.microsoft.com/fwlink/?LinkID=225700). Ce document explique les principales différences entre ceux-là et leurs équivalents dans .NET Framework 4 et les versions antérieures.  
  
 Si vous créez une application du [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], vous devez utiliser les types et membres de réflexion dans [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]. Ces types et membres étant également disponibles, mais pas obligatoires, pour les applications de bureau, il est possible d'utiliser le même code pour les deux types d'applications.  
  
## <a name="typeinfo-and-assembly-loading"></a>TypeInfo et chargement des assemblys  
 Dans [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], la classe <xref:System.Reflection.TypeInfo> contient certaines fonctionnalités de la classe <xref:System.Type> de .NET Framework 4. Un objet <xref:System.Type> représente une référence à la définition d'un type, tandis qu'un objet <xref:System.Reflection.TypeInfo> représente la définition de ce type. Cela vous permet de manipuler des objets <xref:System.Type> sans obliger le runtime à charger l'assembly qu'ils référencent. L'obtention de l'objet <xref:System.Reflection.TypeInfo> associé force le chargement de l'assembly.  
  
 <xref:System.Reflection.TypeInfo> contient bon nombre des membres disponibles sur <xref:System.Type>, et de nombreuses propriétés de réflexion de [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] retournent des collections d'objets <xref:System.Reflection.TypeInfo>. Pour obtenir un objet <xref:System.Reflection.TypeInfo> à partir d'un objet <xref:System.Type>, utilisez la méthode <xref:System.Reflection.IReflectableType.GetTypeInfo%2A>.  
  
## <a name="query-methods"></a>Méthodes de requête  
 Dans [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], utilisez les propriétés de réflexion qui retournent des collections <xref:System.Collections.Generic.IEnumerable%601> au lieu de méthodes qui retournent des tableaux. Les contextes de réflexion peuvent implémenter le parcours différé de ces collections pour de grands assemblys ou types.  
  
 Les propriétés de réflexion retournent uniquement les méthodes déclarées sur un objet particulier au lieu de parcourir l'arborescence d'héritage. De plus, elles n'utilisent pas de paramètres <xref:System.Reflection.BindingFlags> pour le filtrage. Le filtrage s'effectue dans le code utilisateur, en utilisant des requêtes LINQ sur les collections retournées. Pour les objets réflexion provenant du runtime (par exemple, les résultats de `typeof(Object)`), il est plus efficace de parcourir l'arborescence d'héritage en utilisant les méthodes d'assistance de la classe <xref:System.Reflection.RuntimeReflectionExtensions>. Les consommateurs des objets provenant de contextes de réflexion personnalisés ne peuvent pas utiliser ces méthodes, et doivent parcourir l'arborescence d'héritage eux-mêmes.  
  
## <a name="restrictions"></a>Restrictions  
 Dans une application du [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], l'accès à certains types et membres de .NET Framework est restreint. Par exemple, vous ne pouvez pas appeler les méthodes .NET Framework qui ne sont pas incluses dans [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], à l'aide d'un objet <xref:System.Reflection.MethodInfo>. En outre, certains types et membres qui ne sont pas considérés comme sécurisés dans le contexte d'une application du [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] sont bloqués, comme le sont les membres <xref:System.Runtime.InteropServices.Marshal> et <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal>. Cette restriction concerne uniquement les types et membres de .NET Framework. Vous pouvez appeler votre code ou un code tiers de façon habituelle.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise les types et membres de réflexion dans [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] pour récupérer les méthodes et propriétés du type <xref:System.Globalization.Calendar>, y compris les méthodes et propriétés héritées. Pour exécuter ce code, collez-le dans le fichier de code d’une page [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] qui contient un contrôle <xref:Windows.UI.Xaml.Controls.TextBlock?displayProperty=nameWithType> nommé `textblock1` dans un projet Reflection. Si vous collez ce code dans un projet avec un nom différent, veillez à modifier le nom de l'espace de noms pour refléter celui du projet.  
  
 [!code-csharp[System.ReflectionWinStoreApp#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflectionwinstoreapp/cs/mainpage.xaml.cs#1)]
 [!code-vb[System.ReflectionWinStoreApp#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflectionwinstoreapp/vb/mainpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Réflexion](../../../docs/framework/reflection-and-codedom/reflection.md)
- [.NET pour les applications du Windows Store : API prises en charge](https://go.microsoft.com/fwlink/?LinkID=225700)
