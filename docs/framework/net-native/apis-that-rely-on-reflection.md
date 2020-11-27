---
title: API qui s'appuient sur la réflexion
ms.date: 03/30/2017
ms.assetid: f9532629-6594-4a41-909f-d083f30a42f3
ms.openlocfilehash: 2c361962f4570200d63037a68ef39b0c982bd5f7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251137"
---
# <a name="apis-that-rely-on-reflection"></a><span data-ttu-id="4d2fd-102">API qui s'appuient sur la réflexion</span><span class="sxs-lookup"><span data-stu-id="4d2fd-102">APIs That Rely on Reflection</span></span>

<span data-ttu-id="4d2fd-103">Dans certains cas, l’utilisation de la réflexion dans le code n’est pas évidente, de sorte que la chaîne d’outils .NET Native ne conserve pas les métadonnées nécessaires au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="4d2fd-103">In some cases, the use of reflection in code isn't obvious, and so the .NET Native tool chain doesn't preserve metadata that is needed at run time.</span></span> <span data-ttu-id="4d2fd-104">Cette rubrique décrit certaines API courantes ou des modèles de programmation courants qui ne sont pas considérés comme faisant partie de l'API de réflexion, mais dont l'exécution s'appuie sur la réflexion.</span><span class="sxs-lookup"><span data-stu-id="4d2fd-104">This topic covers some common APIs or common programming patterns that aren't considered part of the reflection API but that rely on reflection to execute successfully.</span></span> <span data-ttu-id="4d2fd-105">Si vous les utilisez dans votre code source, vous pouvez ajouter des informations les concernant au fichier de directives runtime (.rd.xml) pour que les appels de ces API ne lèvent pas d’exceptions, telles que [MissingMetadataException](missingmetadataexception-class-net-native.md), au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="4d2fd-105">If you use them in your source code, you can add information about them to the runtime directives (.rd.xml) file so that calls to these APIs do not throw a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception or some other exception at run time.</span></span>  
  
## <a name="typemakegenerictype-method"></a><span data-ttu-id="4d2fd-106">Méthode Type.MakeGenericType</span><span class="sxs-lookup"><span data-stu-id="4d2fd-106">Type.MakeGenericType method</span></span>  

 <span data-ttu-id="4d2fd-107">Vous pouvez instancier dynamiquement un type générique `AppClass<T>` en appelant la méthode <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> à l'aide d'un code tel que celui-ci :</span><span class="sxs-lookup"><span data-stu-id="4d2fd-107">You can dynamically instantiate a generic type `AppClass<T>` by calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 <span data-ttu-id="4d2fd-108">Pour que ce code s'exécute correctement, plusieurs éléments de métadonnées sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="4d2fd-108">For this code to succeed at run time, several items of metadata are required.</span></span> <span data-ttu-id="4d2fd-109">Le premier est constitué des métadonnées `Browse` pour le type générique non instancié, `AppClass<T>` :</span><span class="sxs-lookup"><span data-stu-id="4d2fd-109">The first is `Browse` metadata for the uninstantiated generic type, `AppClass<T>`:</span></span>  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 <span data-ttu-id="4d2fd-110">Il permet à l'appel de méthode <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> de réussir et de retourner un objet <xref:System.Type> valide.</span><span class="sxs-lookup"><span data-stu-id="4d2fd-110">This allows the <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> method call to succeed and return a valid <xref:System.Type> object.</span></span>  
  
 <span data-ttu-id="4d2fd-111">Toutefois, même quand vous ajoutez des métadonnées pour le type générique non instancié, l’appel de la méthode <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> lève une exception [MissingMetadataException](missingmetadataexception-class-net-native.md) :</span><span class="sxs-lookup"><span data-stu-id="4d2fd-111">But even when you add metadata for the uninstantiated generic type, calling the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method throws a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception:</span></span>  
  
<span data-ttu-id="4d2fd-112">Impossible d’effectuer cette opération, car les métadonnées pour le type suivant ont été supprimées pour des raisons de performances :</span><span class="sxs-lookup"><span data-stu-id="4d2fd-112">This operation cannot be carried out as metadata for the following type was removed for performance reasons:</span></span>  
  
<span data-ttu-id="4d2fd-113">`App1.AppClass`1<System. Int32>».</span><span class="sxs-lookup"><span data-stu-id="4d2fd-113">`App1.AppClass`1<System.Int32>\`.</span></span>  
  
 <span data-ttu-id="4d2fd-114">Vous pouvez ajouter la directive runtime suivante au fichier de directives runtime pour ajouter des métadonnées `Activate` pour l'instanciation spécifique sur `AppClass<T>` de <xref:System.Int32?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="4d2fd-114">You can add the following run-time directive to the runtime directives file to add `Activate` metadata for the specific instantiation over `AppClass<T>` of <xref:System.Int32?displayProperty=nameWithType>:</span></span>  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"
                   Activate="Required Public" />  
```  
  
 <span data-ttu-id="4d2fd-115">Chaque instanciation de `AppClass<T>` nécessite sa propre directive si elle est créée avec la méthode <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> et qu’elle n’est pas utilisée de manière statique.</span><span class="sxs-lookup"><span data-stu-id="4d2fd-115">Each different instantiation over `AppClass<T>` requires a separate directive if it is being created with the <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> method and not used statically.</span></span>  
  
## <a name="methodinfomakegenericmethod-method"></a><span data-ttu-id="4d2fd-116">Méthode MethodInfo.MakeGenericMethod</span><span class="sxs-lookup"><span data-stu-id="4d2fd-116">MethodInfo.MakeGenericMethod method</span></span>  

 <span data-ttu-id="4d2fd-117">Dans le cas d'une classe `Class1` avec une méthode générique `GetMethod<T>(T t)`, `GetMethod` peut être appelée par réflexion à l'aide d'un code tel que celui-ci :</span><span class="sxs-lookup"><span data-stu-id="4d2fd-117">Given a class `Class1` with a generic method `GetMethod<T>(T t)`, `GetMethod` can be invoked through reflection by using code like this:</span></span>  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 <span data-ttu-id="4d2fd-118">Pour s'exécuter correctement, ce code nécessite plusieurs éléments de métadonnées :</span><span class="sxs-lookup"><span data-stu-id="4d2fd-118">To run successfully, this code requires several items of metadata:</span></span>  
  
- <span data-ttu-id="4d2fd-119">Les métadonnées `Browse` pour le type dont vous souhaitez appeler la méthode.</span><span class="sxs-lookup"><span data-stu-id="4d2fd-119">`Browse` metadata for the type whose method you want to call.</span></span>  
  
- <span data-ttu-id="4d2fd-120">Les métadonnées `Browse` pour la méthode que vous souhaitez appeler.</span><span class="sxs-lookup"><span data-stu-id="4d2fd-120">`Browse` metadata for the method you want to call.</span></span>  <span data-ttu-id="4d2fd-121">S'il s'agit d'une méthode publique, l'ajout de métadonnées `Browse` publiques pour le type conteneur comprend également la méthode.</span><span class="sxs-lookup"><span data-stu-id="4d2fd-121">If it is a public method, adding public `Browse` metadata for the containing type includes the method, too.</span></span>  
  
- <span data-ttu-id="4d2fd-122">Métadonnées dynamiques pour la méthode que vous souhaitez appeler, afin que le délégué d’appel de réflexion ne soit pas supprimé par la chaîne d’outils .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4d2fd-122">Dynamic metadata for the method you want to call, so that the reflection invocation delegate is not removed by the .NET Native tool chain.</span></span> <span data-ttu-id="4d2fd-123">Si des métadonnées dynamiques sont manquantes pour la méthode, l'exception suivante est levée quand la méthode <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> est appelée :</span><span class="sxs-lookup"><span data-stu-id="4d2fd-123">If dynamic metadata is missing for the method, the following exception is thrown when the <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> method is called:</span></span>  
  
    ```output
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 <span data-ttu-id="4d2fd-124">Les directives runtime suivantes garantissent que toutes les métadonnées nécessaires sont disponibles :</span><span class="sxs-lookup"><span data-stu-id="4d2fd-124">The following runtime directives ensure that all required metadata is available:</span></span>  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 <span data-ttu-id="4d2fd-125">Une directive `MethodInstantiation` est obligatoire pour chaque instanciation différente de la méthode qui est appelée dynamiquement, et l'élément `Arguments` est mis à jour pour refléter chaque argument d'instanciation différent.</span><span class="sxs-lookup"><span data-stu-id="4d2fd-125">A `MethodInstantiation` directive is required for each different instantiation of the method that is dynamically invoked, and the `Arguments` element is updated to reflect each different instantiation argument.</span></span>  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a><span data-ttu-id="4d2fd-126">Méthodes Array.CreateInstance et Type.MakeTypeArray</span><span class="sxs-lookup"><span data-stu-id="4d2fd-126">Array.CreateInstance and Type.MakeTypeArray methods</span></span>  

 <span data-ttu-id="4d2fd-127">L'exemple suivant appelle les méthodes <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> et <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> sur un type, `Class1`.</span><span class="sxs-lookup"><span data-stu-id="4d2fd-127">The following example calls the <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> methods on a type, `Class1`.</span></span>  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 <span data-ttu-id="4d2fd-128">Si aucune métadonnée de tableau n'est présente, l'erreur suivante se produit :</span><span class="sxs-lookup"><span data-stu-id="4d2fd-128">If no array metadata is present, the following error results:</span></span>  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 <span data-ttu-id="4d2fd-129">Les métadonnées `Browse` pour le type de tableau sont nécessaires à son instanciation de manière dynamique.</span><span class="sxs-lookup"><span data-stu-id="4d2fd-129">`Browse` metadata for the array type is required to dynamically instantiate it.</span></span>  <span data-ttu-id="4d2fd-130">La directive runtime suivante permet l'instanciation dynamique de `Class1[]`.</span><span class="sxs-lookup"><span data-stu-id="4d2fd-130">The following runtime directive allows dynamic instantiation of `Class1[]`.</span></span>  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="4d2fd-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d2fd-131">See also</span></span>

- [<span data-ttu-id="4d2fd-132">Prise en main</span><span class="sxs-lookup"><span data-stu-id="4d2fd-132">Getting Started</span></span>](getting-started-with-net-native.md)
- [<span data-ttu-id="4d2fd-133">Guide de référence du fichier de configuration des directives runtime (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="4d2fd-133">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
