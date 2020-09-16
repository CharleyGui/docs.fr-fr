---
title: Exemple de classe COM - Guide de programmation C#
description: Découvrez comment exposer une classe en tant qu’objet COM en C#. Cet exemple ajoute du code dans un fichier. cs à un projet et définit la propriété inscrire pour COM Interop.
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: d49d391f5ea7717e0c36782be65cfb2ae154b843
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90542794"
---
# <a name="example-com-class-c-programming-guide"></a><span data-ttu-id="ec5bf-104">Exemple de classe COM (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="ec5bf-104">Example COM Class (C# Programming Guide)</span></span>
<span data-ttu-id="ec5bf-105">Voici un exemple de classe pouvant être exposée en tant qu’objet COM.</span><span class="sxs-lookup"><span data-stu-id="ec5bf-105">The following is an example of a class that you would expose as a COM object.</span></span> <span data-ttu-id="ec5bf-106">Après avoir placé ce code dans un fichier .cs et l’avoir ajouté à votre projet, affectez la valeur **True** à la propriété **Inscrire pour COM Interop**.</span><span class="sxs-lookup"><span data-stu-id="ec5bf-106">After this code has been placed in a .cs file and added to your project, set the **Register for COM Interop** property to **True**.</span></span> <span data-ttu-id="ec5bf-107">Pour plus d’informations, consultez [Guide pratique pour inscrire un composant pour COM Interop](/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="ec5bf-107">For more information, see [How to: Register a Component for COM Interop](/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).</span></span>
  
 <span data-ttu-id="ec5bf-108">L’exposition d’objets Visual C# à COM nécessite de déclarer une interface de classe, une interface d’événements si nécessaire, et la classe proprement dite.</span><span class="sxs-lookup"><span data-stu-id="ec5bf-108">Exposing Visual C# objects to COM requires declaring a class interface, an events interface if it is required, and the class itself.</span></span> <span data-ttu-id="ec5bf-109">Les membres de classe doivent suivre ces règles pour être visibles par COM :</span><span class="sxs-lookup"><span data-stu-id="ec5bf-109">Class members must follow these rules to be visible to COM:</span></span>  
  
- <span data-ttu-id="ec5bf-110">La classe doit être publique.</span><span class="sxs-lookup"><span data-stu-id="ec5bf-110">The class must be public.</span></span>  
  
- <span data-ttu-id="ec5bf-111">Les propriétés, méthodes et événements doivent être publics.</span><span class="sxs-lookup"><span data-stu-id="ec5bf-111">Properties, methods, and events must be public.</span></span>  
  
- <span data-ttu-id="ec5bf-112">Les propriétés et méthodes doivent être déclarées dans l’interface de classe.</span><span class="sxs-lookup"><span data-stu-id="ec5bf-112">Properties and methods must be declared on the class interface.</span></span>  
  
- <span data-ttu-id="ec5bf-113">Les événements doivent être déclarés dans l’interface d’événement.</span><span class="sxs-lookup"><span data-stu-id="ec5bf-113">Events must be declared in the event interface.</span></span>  
  
 <span data-ttu-id="ec5bf-114">Les autres membres publics de la classe qui ne sont pas déclarés dans ces interfaces ne seront pas visibles par COM, mais ils seront visibles par d’autres objets .NET.</span><span class="sxs-lookup"><span data-stu-id="ec5bf-114">Other public members in the class that are not declared in these interfaces will not be visible to COM, but they will be visible to other .NET objects.</span></span>  
  
 <span data-ttu-id="ec5bf-115">Pour exposer des propriétés et des méthodes à COM, vous devez les déclarer sur l’interface de classe, les marquer avec un attribut `DispId` et les implémenter dans la classe.</span><span class="sxs-lookup"><span data-stu-id="ec5bf-115">To expose properties and methods to COM, you must declare them on the class interface and mark them with a `DispId` attribute, and implement them in the class.</span></span> <span data-ttu-id="ec5bf-116">L’ordre dans lequel les membres sont déclarés dans l’interface est l’ordre utilisé pour la vtable COM.</span><span class="sxs-lookup"><span data-stu-id="ec5bf-116">The order in which the members are declared in the interface is the order used for the COM vtable.</span></span>  
  
 <span data-ttu-id="ec5bf-117">Pour exposer des événements à partir de votre classe, vous devez les déclarer sur l’interface d’événement et les marquer avec un attribut `DispId`.</span><span class="sxs-lookup"><span data-stu-id="ec5bf-117">To expose events from your class, you must declare them on the events interface and mark them with a `DispId` attribute.</span></span> <span data-ttu-id="ec5bf-118">La classe ne doit pas implémenter cette interface.</span><span class="sxs-lookup"><span data-stu-id="ec5bf-118">The class should not implement this interface.</span></span>  
  
 <span data-ttu-id="ec5bf-119">La classe implémente l’interface de classe ; elle peut implémenter plusieurs interfaces, mais la première implémentation sera l’interface de classe par défaut.</span><span class="sxs-lookup"><span data-stu-id="ec5bf-119">The class implements the class interface; it can implement more than one interface, but the first implementation will be the default class interface.</span></span> <span data-ttu-id="ec5bf-120">Implémentez ici les méthodes et propriétés exposées à COM.</span><span class="sxs-lookup"><span data-stu-id="ec5bf-120">Implement the methods and properties exposed to COM here.</span></span> <span data-ttu-id="ec5bf-121">Elles doivent être marquées comme publiques et doivent correspondre aux déclarations dans l’interface de classe.</span><span class="sxs-lookup"><span data-stu-id="ec5bf-121">They must be marked public and must match the declarations in the class interface.</span></span> <span data-ttu-id="ec5bf-122">Vous devez aussi déclarer ici les événements déclenchés par la classe.</span><span class="sxs-lookup"><span data-stu-id="ec5bf-122">Also, declare the events raised by the class here.</span></span> <span data-ttu-id="ec5bf-123">Ils doivent être marqués comme publics et doivent correspondre aux déclarations dans l’interface d’événement.</span><span class="sxs-lookup"><span data-stu-id="ec5bf-123">They must be marked public and must match the declarations in the events interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec5bf-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="ec5bf-124">Example</span></span>  
 [!code-csharp[csProgGuideInterop#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/ExampleCOM.cs#8)]  
  
## <a name="see-also"></a><span data-ttu-id="ec5bf-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec5bf-125">See also</span></span>

- [<span data-ttu-id="ec5bf-126">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="ec5bf-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ec5bf-127">Interopérabilité</span><span class="sxs-lookup"><span data-stu-id="ec5bf-127">Interoperability</span></span>](./index.md)
- [<span data-ttu-id="ec5bf-128">Générer, page du Concepteur de projets (C#)</span><span class="sxs-lookup"><span data-stu-id="ec5bf-128">Build Page, Project Designer (C#)</span></span>](/visualstudio/ide/reference/build-page-project-designer-csharp)
