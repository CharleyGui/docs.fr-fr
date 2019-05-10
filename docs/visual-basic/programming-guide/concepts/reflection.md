---
title: Réflexion (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
ms.openlocfilehash: 8a784f3b8647a74e21299e84e04eb7bda60b9cb6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64627458"
---
# <a name="reflection-visual-basic"></a><span data-ttu-id="42636-102">Réflexion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42636-102">Reflection (Visual Basic)</span></span>
<span data-ttu-id="42636-103">La réflexion fournit des objets (de type <xref:System.Type>) qui décrivent des assemblys, des modules et des types.</span><span class="sxs-lookup"><span data-stu-id="42636-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="42636-104">Vous pouvez utiliser la réflexion pour créer dynamiquement une instance d’un type, lier le type à un objet existant ou obtenir le type à partir d’un objet existant et invoquer ses méthodes ou accéder à ses champs et propriétés.</span><span class="sxs-lookup"><span data-stu-id="42636-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="42636-105">Si vous utilisez des attributs dans votre code, la réflexion vous permet d’y accéder.</span><span class="sxs-lookup"><span data-stu-id="42636-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="42636-106">Pour plus d’informations, consultez [Attributs](../../../standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="42636-106">For more information, see [Attributes](../../../standard/attributes/index.md).</span></span>  
  
 <span data-ttu-id="42636-107">Voici un exemple simple de réflexion utilisant la méthode statique `GetType`, héritée par tous les types à partir de la classe de base `Object`, pour obtenir le type d’une variable :</span><span class="sxs-lookup"><span data-stu-id="42636-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 <span data-ttu-id="42636-108">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="42636-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="42636-109">L’exemple suivant utilise la réflexion pour obtenir le nom complet de l’assembly chargé.</span><span class="sxs-lookup"><span data-stu-id="42636-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 <span data-ttu-id="42636-110">La sortie est la suivante :</span><span class="sxs-lookup"><span data-stu-id="42636-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a><span data-ttu-id="42636-111">Vue d’ensemble de la réflexion</span><span class="sxs-lookup"><span data-stu-id="42636-111">Reflection Overview</span></span>  
 <span data-ttu-id="42636-112">La réflexion est utile dans les situations suivantes :</span><span class="sxs-lookup"><span data-stu-id="42636-112">Reflection is useful in the following situations:</span></span>  
  
- <span data-ttu-id="42636-113">Lorsque vous devez accéder à des attributs dans les métadonnées de votre programme.</span><span class="sxs-lookup"><span data-stu-id="42636-113">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="42636-114">Pour plus d’informations, consultez [Récupération des informations stockées dans les attributs](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="42636-114">For more information, see [Retrieving Information Stored in Attributes](../../../standard/attributes/retrieving-information-stored-in-attributes.md).</span></span>  
  
- <span data-ttu-id="42636-115">Pour examiner et instancier des types dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="42636-115">For examining and instantiating types in an assembly.</span></span>  
  
- <span data-ttu-id="42636-116">Pour créer de nouveaux types au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="42636-116">For building new types at runtime.</span></span> <span data-ttu-id="42636-117">Utilisez des classes dans <xref:System.Reflection.Emit>.</span><span class="sxs-lookup"><span data-stu-id="42636-117">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
- <span data-ttu-id="42636-118">Pour effectuer une liaison tardive, en accédant aux méthodes sur les types créés au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="42636-118">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="42636-119">Consultez la rubrique [Chargement et utilisation dynamiques des types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span><span class="sxs-lookup"><span data-stu-id="42636-119">See the topic [Dynamically Loading and Using Types](../../../framework/reflection-and-codedom/dynamically-loading-and-using-types.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="42636-120">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="42636-120">Related Sections</span></span>  
 <span data-ttu-id="42636-121">Pour plus d'informations :</span><span class="sxs-lookup"><span data-stu-id="42636-121">For more information:</span></span>  
  
- [<span data-ttu-id="42636-122">Réflexion</span><span class="sxs-lookup"><span data-stu-id="42636-122">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
  
- [<span data-ttu-id="42636-123">Affichage des informations de type</span><span class="sxs-lookup"><span data-stu-id="42636-123">Viewing Type Information</span></span>](../../../framework/reflection-and-codedom/viewing-type-information.md)  
  
- [<span data-ttu-id="42636-124">Réflexion et types génériques</span><span class="sxs-lookup"><span data-stu-id="42636-124">Reflection and Generic Types</span></span>](../../../framework/reflection-and-codedom/reflection-and-generic-types.md)  
  
- <xref:System.Reflection.Emit>  
  
- [<span data-ttu-id="42636-125">Récupération des informations stockées dans les attributs</span><span class="sxs-lookup"><span data-stu-id="42636-125">Retrieving Information Stored in Attributes</span></span>](../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
  
## <a name="see-also"></a><span data-ttu-id="42636-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42636-126">See also</span></span>

- [<span data-ttu-id="42636-127">Guide de programmation Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42636-127">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="42636-128">Assemblys dans le Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="42636-128">Assemblies in the Common Language Runtime</span></span>](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
