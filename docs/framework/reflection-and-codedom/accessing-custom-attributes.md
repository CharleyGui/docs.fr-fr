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
# <a name="accessing-custom-attributes"></a><span data-ttu-id="4c07b-104">Accès aux attributs personnalisés</span><span class="sxs-lookup"><span data-stu-id="4c07b-104">Accessing Custom Attributes</span></span>
<span data-ttu-id="4c07b-105">Une fois que des attributs associés aux éléments de programme, la réflexion peut être utilisée pour interroger leur existence et leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="4c07b-105">After attributes have been associated with program elements, reflection can be used to query their existence and values.</span></span> <span data-ttu-id="4c07b-106">Dans le .NET Framework version 1.0 et 1.1, les attributs personnalisés sont examinés dans le contexte d’exécution.</span><span class="sxs-lookup"><span data-stu-id="4c07b-106">In the .NET Framework version 1.0 and 1.1, custom attributes are examined in the execution context.</span></span> <span data-ttu-id="4c07b-107">Le .NET Framework version 2.0 fournit un nouveau contexte de chargement, le contexte de réflexion uniquement, qui peut être utilisé pour examiner le code qui ne peut pas être chargé pour l’exécution.</span><span class="sxs-lookup"><span data-stu-id="4c07b-107">The .NET Framework version 2.0 provides a new load context, the reflection-only context, which can be used to examine code that cannot be loaded for execution.</span></span>  
  
## <a name="the-reflection-only-context"></a><span data-ttu-id="4c07b-108">Le contexte de réflexion uniquement</span><span class="sxs-lookup"><span data-stu-id="4c07b-108">The Reflection-Only Context</span></span>  
 <span data-ttu-id="4c07b-109">Le code chargé dans le contexte de réflexion uniquement ne peut pas être exécuté.</span><span class="sxs-lookup"><span data-stu-id="4c07b-109">Code loaded into the reflection-only context cannot be executed.</span></span> <span data-ttu-id="4c07b-110">Cela signifie que des instances d’attributs personnalisés ne peuvent pas être créées, car cela nécessiterait l’exécution de leurs constructeurs.</span><span class="sxs-lookup"><span data-stu-id="4c07b-110">This means that instances of custom attributes cannot be created, because that would require executing their constructors.</span></span> <span data-ttu-id="4c07b-111">Pour charger et examiner des attributs personnalisés dans le contexte de réflexion uniquement, utilisez la classe <xref:System.Reflection.CustomAttributeData>.</span><span class="sxs-lookup"><span data-stu-id="4c07b-111">To load and examine custom attributes in the reflection-only context, use the <xref:System.Reflection.CustomAttributeData> class.</span></span> <span data-ttu-id="4c07b-112">Vous pouvez obtenir des instances de cette classe à l’aide de la surcharge appropriée de la méthode statique <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4c07b-112">You can obtain instances of this class by using the appropriate overload of the static <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4c07b-113">Consultez [Comment : charger des assemblys dans le contexte de réflexion uniquement](how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="4c07b-113">See [How to: Load Assemblies into the Reflection-Only Context](how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
## <a name="the-execution-context"></a><span data-ttu-id="4c07b-114">Le contexte d’exécution</span><span class="sxs-lookup"><span data-stu-id="4c07b-114">The Execution Context</span></span>  
 <span data-ttu-id="4c07b-115">Les principales méthodes de réflexion pour interroger les attributs dans le contexte d’exécution sont <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> et <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4c07b-115">The main reflection methods to query attributes in the execution context are <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> and <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="4c07b-116">L’accessibilité d’un attribut personnalisé est vérifiée par rapport à l’assembly dans lequel il est attaché.</span><span class="sxs-lookup"><span data-stu-id="4c07b-116">The accessibility of a custom attribute is checked with respect to the assembly in which it is attached.</span></span> <span data-ttu-id="4c07b-117">Cela équivaut à vérifier si une méthode sur un type dans l’assembly dans lequel l’attribut personnalisé est attaché peut appeler le constructeur de l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="4c07b-117">This is equivalent to checking whether a method on a type in the assembly in which the custom attribute is attached can call the constructor of the custom attribute.</span></span>  
  
 <span data-ttu-id="4c07b-118">Les méthodes comme <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> vérifient la visibilité et l’accessibilité de l’argument de type.</span><span class="sxs-lookup"><span data-stu-id="4c07b-118">Methods such as <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> check the visibility and accessibility of the type argument.</span></span> <span data-ttu-id="4c07b-119">Seul le code dans l’assembly qui contient le type défini par l’utilisateur peut récupérer un attribut personnalisé de ce type à l’aide de **GetCustomAttributes**.</span><span class="sxs-lookup"><span data-stu-id="4c07b-119">Only code in the assembly that contains the user-defined type can retrieve a custom attribute of that type using **GetCustomAttributes**.</span></span>  
  
 <span data-ttu-id="4c07b-120">L’exemple C# suivant est un modèle de conception d’attribut personnalisé classique.</span><span class="sxs-lookup"><span data-stu-id="4c07b-120">The following C# example is a typical custom attribute design pattern.</span></span> <span data-ttu-id="4c07b-121">Il illustre le modèle de réflexion d’attribut personnalisé du runtime.</span><span class="sxs-lookup"><span data-stu-id="4c07b-121">It illustrates the runtime custom attribute reflection model.</span></span>  
  
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
  
 <span data-ttu-id="4c07b-122">Si le runtime tente de récupérer les attributs personnalisés pour le type d’attribut personnalisé public <xref:System.ComponentModel.DescriptionAttribute> attaché à la méthode **GetLanguage**, il effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="4c07b-122">If the runtime is attempting to retrieve the custom attributes for the public custom attribute type <xref:System.ComponentModel.DescriptionAttribute> attached to the **GetLanguage** method, it performs the following actions:</span></span>  
  
1. <span data-ttu-id="4c07b-123">Le runtime vérifie que l’argument de type **DescriptionAttribute** pour **Type.GetCustomAttributes**(Type *type*) est public, et est par conséquent visible et accessible.</span><span class="sxs-lookup"><span data-stu-id="4c07b-123">The runtime checks that the type argument **DescriptionAttribute** to **Type.GetCustomAttributes**(Type *type*) is public, and therefore is visible and accessible.</span></span>  
  
2. <span data-ttu-id="4c07b-124">Le runtime vérifie que le type défini par l’utilisateur **MyDescriptionAttribute** qui est dérivé de **DescriptionAttribute** est visible et accessible dans l’assembly **System.Web.DLL**, où il est attaché à la méthode **GetLanguage**().</span><span class="sxs-lookup"><span data-stu-id="4c07b-124">The runtime checks that the user-defined type **MyDescriptionAttribute** that is derived from **DescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly, where it is attached to the method **GetLanguage**().</span></span>  
  
3. <span data-ttu-id="4c07b-125">Le runtime vérifie que le constructeur de **MyDescriptionAttribute** est visible et accessible dans l’assembly **System.Web.DLL**.</span><span class="sxs-lookup"><span data-stu-id="4c07b-125">The runtime checks that the constructor of **MyDescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly.</span></span>  
  
4. <span data-ttu-id="4c07b-126">Le runtime appelle le constructeur de **MyDescriptionAttribute** avec les paramètres de l’attribut personnalisé et retourne le nouvel objet à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="4c07b-126">The runtime calls the constructor of **MyDescriptionAttribute** with the custom attribute parameters and returns the new object to the caller.</span></span>  
  
 <span data-ttu-id="4c07b-127">Le modèle de réflexion d’attribut personnalisé peut laisser fuiter des instances de types définis par l’utilisateur en dehors de l’assembly dans lequel le type est défini.</span><span class="sxs-lookup"><span data-stu-id="4c07b-127">The custom attribute reflection model could leak instances of user-defined types outside the assembly in which the type is defined.</span></span> <span data-ttu-id="4c07b-128">Cela ne diffère pas des membres de la bibliothèque système du runtime qui retournent des instances de types définis par l’utilisateur, comme <xref:System.Type.GetMethods%2A?displayProperty=nameWithType>, qui retourne un tableau d’objets **RuntimeMethodInfo**.</span><span class="sxs-lookup"><span data-stu-id="4c07b-128">This is no different from the members in the runtime system library that return instances of user-defined types, such as <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> returning an array of **RuntimeMethodInfo** objects.</span></span> <span data-ttu-id="4c07b-129">Pour empêcher un client de découvrir des informations relatives à un type d’attribut personnalisé défini par l’utilisateur, définissez les membres du type comme étant non publics.</span><span class="sxs-lookup"><span data-stu-id="4c07b-129">To prevent a client from discovering information about a user-defined custom attribute type, define the type's members to be nonpublic.</span></span>  
  
 <span data-ttu-id="4c07b-130">L’exemple suivant montre comment utiliser simplement la réflexion pour accéder à des attributs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="4c07b-130">The following example demonstrates the basic way of using reflection to get access to custom attributes.</span></span>  
  
 [!code-cpp[CustomAttributeData#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source2.cpp#2)]
 [!code-csharp[CustomAttributeData#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source2.cs#2)]
 [!code-vb[CustomAttributeData#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="4c07b-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c07b-131">See also</span></span>

- <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [<span data-ttu-id="4c07b-132">Affichage des informations de type</span><span class="sxs-lookup"><span data-stu-id="4c07b-132">Viewing Type Information</span></span>](viewing-type-information.md)
- [<span data-ttu-id="4c07b-133">Considérations sur la sécurité de la réflexion</span><span class="sxs-lookup"><span data-stu-id="4c07b-133">Security Considerations for Reflection</span></span>](security-considerations-for-reflection.md)
