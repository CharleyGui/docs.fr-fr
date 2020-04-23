---
title: Accès aux attributs personnalisés
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
ms.openlocfilehash: a5651e9dc8cf40e737dd523ec5d29e876a9c0765
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130300"
---
# <a name="accessing-custom-attributes"></a><span data-ttu-id="13ea3-102">Accès aux attributs personnalisés</span><span class="sxs-lookup"><span data-stu-id="13ea3-102">Accessing Custom Attributes</span></span>
<span data-ttu-id="13ea3-103">Une fois que des attributs associés aux éléments de programme, la réflexion peut être utilisée pour interroger leur existence et leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="13ea3-103">After attributes have been associated with program elements, reflection can be used to query their existence and values.</span></span> <span data-ttu-id="13ea3-104">Dans le .NET Framework version 1.0 et 1.1, les attributs personnalisés sont examinés dans le contexte d’exécution.</span><span class="sxs-lookup"><span data-stu-id="13ea3-104">In the .NET Framework version 1.0 and 1.1, custom attributes are examined in the execution context.</span></span> <span data-ttu-id="13ea3-105">Le .NET Framework version 2.0 fournit un nouveau contexte de chargement, le contexte de réflexion uniquement, qui peut être utilisé pour examiner le code qui ne peut pas être chargé pour l’exécution.</span><span class="sxs-lookup"><span data-stu-id="13ea3-105">The .NET Framework version 2.0 provides a new load context, the reflection-only context, which can be used to examine code that cannot be loaded for execution.</span></span>  
  
## <a name="the-reflection-only-context"></a><span data-ttu-id="13ea3-106">Le contexte de réflexion uniquement</span><span class="sxs-lookup"><span data-stu-id="13ea3-106">The Reflection-Only Context</span></span>  
 <span data-ttu-id="13ea3-107">Le code chargé dans le contexte de réflexion uniquement ne peut pas être exécuté.</span><span class="sxs-lookup"><span data-stu-id="13ea3-107">Code loaded into the reflection-only context cannot be executed.</span></span> <span data-ttu-id="13ea3-108">Cela signifie que des instances d’attributs personnalisés ne peuvent pas être créées, car cela nécessiterait l’exécution de leurs constructeurs.</span><span class="sxs-lookup"><span data-stu-id="13ea3-108">This means that instances of custom attributes cannot be created, because that would require executing their constructors.</span></span> <span data-ttu-id="13ea3-109">Pour charger et examiner des attributs personnalisés dans le contexte de réflexion uniquement, utilisez la classe <xref:System.Reflection.CustomAttributeData>.</span><span class="sxs-lookup"><span data-stu-id="13ea3-109">To load and examine custom attributes in the reflection-only context, use the <xref:System.Reflection.CustomAttributeData> class.</span></span> <span data-ttu-id="13ea3-110">Vous pouvez obtenir des instances de cette classe à l’aide de la surcharge appropriée de la méthode statique <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="13ea3-110">You can obtain instances of this class by using the appropriate overload of the static <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="13ea3-111">Consultez [Comment : charger des assemblys dans le contexte de réflexion uniquement](how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="13ea3-111">See [How to: Load Assemblies into the Reflection-Only Context](how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
## <a name="the-execution-context"></a><span data-ttu-id="13ea3-112">Le contexte d’exécution</span><span class="sxs-lookup"><span data-stu-id="13ea3-112">The Execution Context</span></span>  
 <span data-ttu-id="13ea3-113">Les principales méthodes de réflexion pour interroger les attributs dans le contexte d’exécution sont <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> et <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="13ea3-113">The main reflection methods to query attributes in the execution context are <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType> and <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="13ea3-114">L’accessibilité d’un attribut personnalisé est vérifiée par rapport à l’assembly dans lequel il est attaché.</span><span class="sxs-lookup"><span data-stu-id="13ea3-114">The accessibility of a custom attribute is checked with respect to the assembly in which it is attached.</span></span> <span data-ttu-id="13ea3-115">Cela équivaut à vérifier si une méthode sur un type dans l’assembly dans lequel l’attribut personnalisé est attaché peut appeler le constructeur de l’attribut personnalisé.</span><span class="sxs-lookup"><span data-stu-id="13ea3-115">This is equivalent to checking whether a method on a type in the assembly in which the custom attribute is attached can call the constructor of the custom attribute.</span></span>  
  
 <span data-ttu-id="13ea3-116">Les méthodes comme <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> vérifient la visibilité et l’accessibilité de l’argument de type.</span><span class="sxs-lookup"><span data-stu-id="13ea3-116">Methods such as <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=nameWithType> check the visibility and accessibility of the type argument.</span></span> <span data-ttu-id="13ea3-117">Seul le code dans l’assembly qui contient le type défini par l’utilisateur peut récupérer un attribut personnalisé de ce type à l’aide de **GetCustomAttributes**.</span><span class="sxs-lookup"><span data-stu-id="13ea3-117">Only code in the assembly that contains the user-defined type can retrieve a custom attribute of that type using **GetCustomAttributes**.</span></span>  
  
 <span data-ttu-id="13ea3-118">L’exemple C# suivant est un modèle de conception d’attribut personnalisé classique.</span><span class="sxs-lookup"><span data-stu-id="13ea3-118">The following C# example is a typical custom attribute design pattern.</span></span> <span data-ttu-id="13ea3-119">Il illustre le modèle de réflexion d’attribut personnalisé du runtime.</span><span class="sxs-lookup"><span data-stu-id="13ea3-119">It illustrates the runtime custom attribute reflection model.</span></span>  
  
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
  
 <span data-ttu-id="13ea3-120">Si le runtime tente de récupérer les attributs personnalisés pour le type d’attribut personnalisé public <xref:System.ComponentModel.DescriptionAttribute> attaché à la méthode **GetLanguage**, il effectue les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="13ea3-120">If the runtime is attempting to retrieve the custom attributes for the public custom attribute type <xref:System.ComponentModel.DescriptionAttribute> attached to the **GetLanguage** method, it performs the following actions:</span></span>  
  
1. <span data-ttu-id="13ea3-121">Le runtime vérifie que l’argument de type **DescriptionAttribute** pour **Type.GetCustomAttributes**(Type *type*) est public, et est par conséquent visible et accessible.</span><span class="sxs-lookup"><span data-stu-id="13ea3-121">The runtime checks that the type argument **DescriptionAttribute** to **Type.GetCustomAttributes**(Type *type*) is public, and therefore is visible and accessible.</span></span>  
  
2. <span data-ttu-id="13ea3-122">Le runtime vérifie que le type défini par l’utilisateur **MyDescriptionAttribute** qui est dérivé de **DescriptionAttribute** est visible et accessible dans l’assembly **System.Web.DLL**, où il est attaché à la méthode **GetLanguage**().</span><span class="sxs-lookup"><span data-stu-id="13ea3-122">The runtime checks that the user-defined type **MyDescriptionAttribute** that is derived from **DescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly, where it is attached to the method **GetLanguage**().</span></span>  
  
3. <span data-ttu-id="13ea3-123">Le runtime vérifie que le constructeur de **MyDescriptionAttribute** est visible et accessible dans l’assembly **System.Web.DLL**.</span><span class="sxs-lookup"><span data-stu-id="13ea3-123">The runtime checks that the constructor of **MyDescriptionAttribute** is visible and accessible within the **System.Web.DLL** assembly.</span></span>  
  
4. <span data-ttu-id="13ea3-124">Le runtime appelle le constructeur de **MyDescriptionAttribute** avec les paramètres de l’attribut personnalisé et retourne le nouvel objet à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="13ea3-124">The runtime calls the constructor of **MyDescriptionAttribute** with the custom attribute parameters and returns the new object to the caller.</span></span>  
  
 <span data-ttu-id="13ea3-125">Le modèle de réflexion d’attribut personnalisé peut laisser fuiter des instances de types définis par l’utilisateur en dehors de l’assembly dans lequel le type est défini.</span><span class="sxs-lookup"><span data-stu-id="13ea3-125">The custom attribute reflection model could leak instances of user-defined types outside the assembly in which the type is defined.</span></span> <span data-ttu-id="13ea3-126">Cela ne diffère pas des membres de la bibliothèque système du runtime qui retournent des instances de types définis par l’utilisateur, comme <xref:System.Type.GetMethods%2A?displayProperty=nameWithType>, qui retourne un tableau d’objets **RuntimeMethodInfo**.</span><span class="sxs-lookup"><span data-stu-id="13ea3-126">This is no different from the members in the runtime system library that return instances of user-defined types, such as <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> returning an array of **RuntimeMethodInfo** objects.</span></span> <span data-ttu-id="13ea3-127">Pour empêcher un client de découvrir des informations relatives à un type d’attribut personnalisé défini par l’utilisateur, définissez les membres du type comme étant non publics.</span><span class="sxs-lookup"><span data-stu-id="13ea3-127">To prevent a client from discovering information about a user-defined custom attribute type, define the type's members to be nonpublic.</span></span>  
  
 <span data-ttu-id="13ea3-128">L’exemple suivant montre comment utiliser simplement la réflexion pour accéder à des attributs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="13ea3-128">The following example demonstrates the basic way of using reflection to get access to custom attributes.</span></span>  
  
 [!code-cpp[CustomAttributeData#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source2.cpp#2)]
 [!code-csharp[CustomAttributeData#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source2.cs#2)]
 [!code-vb[CustomAttributeData#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="13ea3-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13ea3-129">See also</span></span>

- <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=nameWithType>
- <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>
- [<span data-ttu-id="13ea3-130">Affichage des informations de type</span><span class="sxs-lookup"><span data-stu-id="13ea3-130">Viewing Type Information</span></span>](viewing-type-information.md)
- [<span data-ttu-id="13ea3-131">Considérations sur la sécurité de la réflexion</span><span class="sxs-lookup"><span data-stu-id="13ea3-131">Security Considerations for Reflection</span></span>](security-considerations-for-reflection.md)
