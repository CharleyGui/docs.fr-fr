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
ms.openlocfilehash: 42bcfd4a1adc66511a1183807c09e77d1448c754
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715883"
---
# <a name="reflection-in-the-net-framework-for-windows-store-apps"></a>Réflexion dans le .NET Framework pour les applications Windows Store

À partir de la .NET Framework 4,5, le .NET Framework comprend un ensemble de types et de membres de réflexion à utiliser dans les applications du Windows 8. x Store. Ces types et membres sont disponibles dans le .NET Framework complet et dans .NET pour les applications du Windows Store. Ce document explique les principales différences entre ceux-là et leurs équivalents dans .NET Framework 4 et les versions antérieures.  
  
 Si vous créez une application Windows 8. x Store, vous devez utiliser les types et membres de réflexion dans .NET pour les applications du Windows 8. x Store. Ces types et membres étant également disponibles, mais pas obligatoires, pour les applications de bureau, il est possible d'utiliser le même code pour les deux types d'applications.  
  
## <a name="typeinfo-and-assembly-loading"></a>TypeInfo et chargement des assemblys  
 Dans .NET pour les applications du Windows 8. x Store, <xref:System.Reflection.TypeInfo> la classe contient certaines fonctionnalités de la classe .NET Framework 4 <xref:System.Type> . Un objet <xref:System.Type> représente une référence à la définition d'un type, tandis qu'un objet <xref:System.Reflection.TypeInfo> représente la définition de ce type. Cela vous permet de manipuler des objets <xref:System.Type> sans obliger le runtime à charger l'assembly qu'ils référencent. L'obtention de l'objet <xref:System.Reflection.TypeInfo> associé force le chargement de l'assembly.  
  
 <xref:System.Reflection.TypeInfo>contient un grand nombre des membres disponibles <xref:System.Type>sur, et la plupart des propriétés de réflexion dans .net pour les applications du Store Windows 8. x <xref:System.Reflection.TypeInfo> retournent des collections d’objets. Pour obtenir un objet <xref:System.Reflection.TypeInfo> à partir d'un objet <xref:System.Type>, utilisez la méthode <xref:System.Reflection.IReflectableType.GetTypeInfo%2A>.  
  
## <a name="query-methods"></a>Méthodes de requête  
 Dans .NET pour les applications du Windows 8. x Store, vous utilisez les propriétés de réflexion <xref:System.Collections.Generic.IEnumerable%601> qui retournent des collections au lieu de méthodes qui retournent des tableaux. Les contextes de réflexion peuvent implémenter le parcours différé de ces collections pour de grands assemblys ou types.  
  
 Les propriétés de réflexion retournent uniquement les méthodes déclarées sur un objet particulier au lieu de parcourir l'arborescence d'héritage. De plus, elles n'utilisent pas de paramètres <xref:System.Reflection.BindingFlags> pour le filtrage. Le filtrage s'effectue dans le code utilisateur, en utilisant des requêtes LINQ sur les collections retournées. Pour les objets réflexion provenant du runtime (par exemple, les résultats de `typeof(Object)`), il est plus efficace de parcourir l'arborescence d'héritage en utilisant les méthodes d'assistance de la classe <xref:System.Reflection.RuntimeReflectionExtensions>. Les consommateurs des objets provenant de contextes de réflexion personnalisés ne peuvent pas utiliser ces méthodes, et doivent parcourir l'arborescence d'héritage eux-mêmes.  
  
## <a name="restrictions"></a>Restrictions  
 Dans une application Windows 8. x Store, l’accès à certains types et membres de .NET Framework est limité. Par exemple, vous ne pouvez pas appeler des méthodes .NET Framework qui ne sont pas incluses dans .NET pour les applications du Windows 8. <xref:System.Reflection.MethodInfo> x Store, à l’aide d’un objet. En outre, certains types et membres qui ne sont pas considérés comme sécurisés dans le contexte d’une application de Store Windows 8. x <xref:System.Runtime.InteropServices.Marshal> sont <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal> bloqués, comme les membres et. Cette restriction concerne uniquement les types et membres de .NET Framework. Vous pouvez appeler votre code ou un code tiers de façon habituelle.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise les types et membres de réflexion dans .NET pour les applications du Windows 8. x Store pour récupérer les méthodes et les <xref:System.Globalization.Calendar> propriétés du type, y compris les méthodes et propriétés héritées. Pour exécuter ce code, collez-le dans le fichier de code d’une page Windows 8. x Store <xref:Windows.UI.Xaml.Controls.TextBlock?displayProperty=nameWithType> qui contient `textblock1` un contrôle nommé dans un projet nommé Reflection. Si vous collez ce code dans un projet avec un nom différent, veillez à modifier le nom de l'espace de noms pour refléter celui du projet.  
  
 [!code-csharp[System.ReflectionWinStoreApp#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.reflectionwinstoreapp/cs/mainpage.xaml.cs#1)]
 [!code-vb[System.ReflectionWinStoreApp#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.reflectionwinstoreapp/vb/mainpage.xaml.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- [Réflexion](reflection.md)
