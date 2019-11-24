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
ms.openlocfilehash: 9aaec282fda0a038d14f3a0cd57e1a8a2855f2ad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448135"
---
# <a name="reflection-in-the-net-framework-for-windows-store-apps"></a>Réflexion dans le .NET Framework pour les applications Windows Store

Starting with the .NET Framework 4.5, the .NET Framework includes a set of reflection types and members for use in Windows 8.x Store apps. These types and members are available in the full .NET Framework as well as in the .NET for Windows Store apps. Ce document explique les principales différences entre ceux-là et leurs équivalents dans .NET Framework 4 et les versions antérieures.  
  
 If you are creating a Windows 8.x Store app, you must use the reflection types and members in the [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]. Ces types et membres étant également disponibles, mais pas obligatoires, pour les applications de bureau, il est possible d'utiliser le même code pour les deux types d'applications.  
  
## <a name="typeinfo-and-assembly-loading"></a>TypeInfo et chargement des assemblys  
 Dans [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], la classe <xref:System.Reflection.TypeInfo> contient certaines fonctionnalités de la classe <xref:System.Type> de .NET Framework 4. Un objet <xref:System.Type> représente une référence à la définition d'un type, tandis qu'un objet <xref:System.Reflection.TypeInfo> représente la définition de ce type. Cela vous permet de manipuler des objets <xref:System.Type> sans obliger le runtime à charger l'assembly qu'ils référencent. L'obtention de l'objet <xref:System.Reflection.TypeInfo> associé force le chargement de l'assembly.  
  
 <xref:System.Reflection.TypeInfo> contient bon nombre des membres disponibles sur <xref:System.Type>, et de nombreuses propriétés de réflexion de [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] retournent des collections d'objets <xref:System.Reflection.TypeInfo>. Pour obtenir un objet <xref:System.Reflection.TypeInfo> à partir d'un objet <xref:System.Type>, utilisez la méthode <xref:System.Reflection.IReflectableType.GetTypeInfo%2A>.  
  
## <a name="query-methods"></a>Méthodes de requête  
 Dans [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], utilisez les propriétés de réflexion qui retournent des collections <xref:System.Collections.Generic.IEnumerable%601> au lieu de méthodes qui retournent des tableaux. Les contextes de réflexion peuvent implémenter le parcours différé de ces collections pour de grands assemblys ou types.  
  
 Les propriétés de réflexion retournent uniquement les méthodes déclarées sur un objet particulier au lieu de parcourir l'arborescence d'héritage. De plus, elles n'utilisent pas de paramètres <xref:System.Reflection.BindingFlags> pour le filtrage. Le filtrage s'effectue dans le code utilisateur, en utilisant des requêtes LINQ sur les collections retournées. Pour les objets réflexion provenant du runtime (par exemple, les résultats de `typeof(Object)`), il est plus efficace de parcourir l'arborescence d'héritage en utilisant les méthodes d'assistance de la classe <xref:System.Reflection.RuntimeReflectionExtensions>. Les consommateurs des objets provenant de contextes de réflexion personnalisés ne peuvent pas utiliser ces méthodes, et doivent parcourir l'arborescence d'héritage eux-mêmes.  
  
## <a name="restrictions"></a>Restrictions  
 In a Windows 8.x Store app, access to some .NET Framework types and members is restricted. Par exemple, vous ne pouvez pas appeler les méthodes .NET Framework qui ne sont pas incluses dans [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)], à l'aide d'un objet <xref:System.Reflection.MethodInfo>. In addition, certain types and members that are not considered safe within the context of a Windows 8.x Store app are blocked, as are <xref:System.Runtime.InteropServices.Marshal> and <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal> members. Cette restriction concerne uniquement les types et membres de .NET Framework. Vous pouvez appeler votre code ou un code tiers de façon habituelle.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise les types et membres de réflexion dans [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] pour récupérer les méthodes et propriétés du type <xref:System.Globalization.Calendar>, y compris les méthodes et propriétés héritées. To run this code, paste it into the code file for a Windows 8.x Store page that contains a <xref:Windows.UI.Xaml.Controls.TextBlock?displayProperty=nameWithType> control named `textblock1` in a project named Reflection. Si vous collez ce code dans un projet avec un nom différent, veillez à modifier le nom de l'espace de noms pour refléter celui du projet.  
  
 [!code-csharp[System.ReflectionWinStoreApp#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflectionwinstoreapp/cs/mainpage.xaml.cs#1)]
 [!code-vb[System.ReflectionWinStoreApp#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflectionwinstoreapp/vb/mainpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Réflexion](reflection.md)
