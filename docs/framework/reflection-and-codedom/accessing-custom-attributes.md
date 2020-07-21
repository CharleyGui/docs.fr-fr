---
title: Accès aux attributs personnalisés
description: Accédez aux attributs personnalisés dans .NET. Une fois que les attributs ont été associés à des éléments de programme, vous pouvez utiliser la réflexion pour interroger leur existence et leurs valeurs.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- custom attributes, accessibility
- attributes [.NET Framework], accessing
- reflection, custom attributes
ms.assetid: 1d8e3398-00d8-47d5-a084-214f9859d3d7
ms.openlocfilehash: 1197fc5149e144d293deda1173e82ca2dadeda7d
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475136"
---
# <a name="accessing-custom-attributes"></a>Accès aux attributs personnalisés
Une fois que des attributs associés aux éléments de programme, la réflexion peut être utilisée pour interroger leur existence et leurs valeurs. Dans le .NET Framework version 1.0 et 1.1, les attributs personnalisés sont examinés dans le contexte d’exécution. Le .NET Framework version 2.0 fournit un nouveau contexte de chargement, le contexte de réflexion uniquement, qui peut être utilisé pour examiner le code qui ne peut pas être chargé pour l’exécution.  
  
## <a name="the-reflection-only-context"></a>Le contexte de réflexion uniquement  
 Le code chargé dans le contexte de réflexion uniquement ne peut pas être exécuté. Cela signifie que des instances d’attributs personnalisés ne peuvent pas être créées, car cela nécessiterait l’exécution de leurs constructeurs. Pour charger et examiner des attributs personnalisés dans le contexte de réflexion uniquement, utilisez la classe <xref:System.Reflection.CustomAttributeData>. Vous pouvez obtenir des instances de cette classe à l’aide de la surcharge appropriée de la méthode statique <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType>. Consultez [Comment : charger des assemblys dans le contexte de réflexion uniquement](how-to-load-assemblies-into-the-reflection-only-context.md).  
  
## <a name="the-execution-context"></a>Le contexte d’exécution  
 Les principales méthodes de réflexion pour interroger les attributs dans le contexte d’exécution sont <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> et <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.  
  
 L’accessibilité d’un attribut personnalisé est vérifiée par rapport à l’assembly dans lequel il est attaché. Cela équivaut à vérifier si une méthode sur un type dans l’assembly dans lequel l’attribut personnalisé est attaché peut appeler le constructeur de l’attribut personnalisé.  
  
 Les méthodes comme <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> vérifient la visibilité et l’accessibilité de l’argument de type. Seul le code dans l’assembly qui contient le type défini par l’utilisateur peut récupérer un attribut personnalisé de ce type à l’aide de **GetCustomAttributes**.  
  
 L’exemple C# suivant est un modèle de conception d’attribut personnalisé classique. Il illustre le modèle de réflexion d’attribut personnalisé du runtime.  
  
```csharp
System.DLL  
public class DescriptionAttribute : Attribute  
{  
}  
  
System.Web.DLL  
internal class MyDescriptionAttribute : DescriptionAttribute  
{  
}  
  
public class LocalizationExtenderProvider  
{  
    [MyDescriptionAttribute(...)]  
    public CultureInfo GetLanguage(...)  
    {  
    }  
}  
```  
  
 Si le runtime tente de récupérer les attributs personnalisés pour le type d’attribut personnalisé public <xref:System.ComponentModel.DescriptionAttribute> attaché à la méthode **GetLanguage**, il effectue les actions suivantes :  
  
1. Le runtime vérifie que l’argument de type **DescriptionAttribute** pour **Type.GetCustomAttributes**(Type *type*) est public, et est par conséquent visible et accessible.  
  
2. Le runtime vérifie que le type défini par l’utilisateur **MyDescriptionAttribute** qui est dérivé de **DescriptionAttribute** est visible et accessible dans l’assembly **System.Web.DLL**, où il est attaché à la méthode **GetLanguage**().  
  
3. Le runtime vérifie que le constructeur de **MyDescriptionAttribute** est visible et accessible dans l’assembly **System.Web.DLL**.  
  
4. Le runtime appelle le constructeur de **MyDescriptionAttribute** avec les paramètres de l’attribut personnalisé et retourne le nouvel objet à l’appelant.  
  
 Le modèle de réflexion d’attribut personnalisé peut laisser fuiter des instances de types définis par l’utilisateur en dehors de l’assembly dans lequel le type est défini. Cela ne diffère pas des membres de la bibliothèque système du runtime qui retournent des instances de types définis par l’utilisateur, comme <xref:System.Type.GetMethods%2A?displayProperty=nameWithType>, qui retourne un tableau d’objets **RuntimeMethodInfo**. Pour empêcher un client de découvrir des informations relatives à un type d’attribut personnalisé défini par l’utilisateur, définissez les membres du type comme étant non publics.  
  
 L’exemple suivant montre comment utiliser simplement la réflexion pour accéder à des attributs personnalisés.  
  
 [!code-cpp[CustomAttributeData#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source2.cpp#2)]
 [!code-csharp[CustomAttributeData#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source2.cs#2)]
 [!code-vb[CustomAttributeData#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source2.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [Affichage des informations de type](viewing-type-information.md)
- [Considérations sur la sécurité de la réflexion](security-considerations-for-reflection.md)
