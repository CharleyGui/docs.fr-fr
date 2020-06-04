---
title: 'Comment : référencer les objets COM à partir de Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], referencing COM objects
- referencing objects, COM objects from Visual Basic
- objects [Visual Basic], referencing
- COM objects, referencing
- interop assemblies
ms.assetid: 9c518fb4-27d9-4112-9e6a-5a7d0210af6f
ms.openlocfilehash: 2e2cbac6fad5e1686b7383c44619b8c6f5326483
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396802"
---
# <a name="how-to-reference-com-objects-from-visual-basic"></a><span data-ttu-id="d26ab-102">Comment : référencer les objets COM à partir de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d26ab-102">How to: Reference COM Objects from Visual Basic</span></span>
<span data-ttu-id="d26ab-103">Dans Visual Basic, l’ajout de références à des objets COM qui ont des bibliothèques de types requiert la création d’un assembly d’interopérabilité pour la bibliothèque COM.</span><span class="sxs-lookup"><span data-stu-id="d26ab-103">In Visual Basic, adding references to COM objects that have type libraries requires the creation of an interop assembly for the COM library.</span></span> <span data-ttu-id="d26ab-104">Les références aux membres de l’objet COM sont routées vers l’assembly d’interopérabilité, puis transmises à l’objet COM réel.</span><span class="sxs-lookup"><span data-stu-id="d26ab-104">References to the members of the COM object are routed to the interop assembly and then forwarded to the actual COM object.</span></span> <span data-ttu-id="d26ab-105">Les réponses de l’objet COM sont routées vers l’assembly d’interopérabilité et transmises à votre application .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d26ab-105">Responses from the COM object are routed to the interop assembly and forwarded to your .NET Framework application.</span></span>  
  
 <span data-ttu-id="d26ab-106">Vous pouvez référencer un objet COM sans utiliser d’assembly d’interopérabilité en incorporant les informations de type de l’objet COM dans un assembly .NET.</span><span class="sxs-lookup"><span data-stu-id="d26ab-106">You can reference a COM object without using an interop assembly by embedding the type information for the COM object in a .NET assembly.</span></span> <span data-ttu-id="d26ab-107">Pour incorporer des informations de type, affectez à la propriété la valeur `Embed Interop Types` `True` pour la référence à l’objet com.</span><span class="sxs-lookup"><span data-stu-id="d26ab-107">To embed type information, set the `Embed Interop Types` property to `True` for the reference to the COM object.</span></span> <span data-ttu-id="d26ab-108">Si vous compilez à l’aide du compilateur de ligne de commande, utilisez l' `/link` option pour référencer la bibliothèque com.</span><span class="sxs-lookup"><span data-stu-id="d26ab-108">If you are compiling by using the command-line compiler, use the `/link` option to reference the COM library.</span></span> <span data-ttu-id="d26ab-109">Pour plus d’informations, consultez [-Link (Visual Basic)](../../reference/command-line-compiler/link.md).</span><span class="sxs-lookup"><span data-stu-id="d26ab-109">For more information, see [-link (Visual Basic)](../../reference/command-line-compiler/link.md).</span></span>  
  
 <span data-ttu-id="d26ab-110">Visual Basic crée automatiquement des assemblys d’interopérabilité lorsque vous ajoutez une référence à une bibliothèque de types à partir de l’environnement de développement intégré (IDE).</span><span class="sxs-lookup"><span data-stu-id="d26ab-110">Visual Basic automatically creates interop assemblies when you add a reference to a type library from the integrated development environment (IDE).</span></span> <span data-ttu-id="d26ab-111">Lorsque vous travaillez à partir de la ligne de commande, vous pouvez utiliser l’utilitaire Tlbimp pour créer manuellement des assemblys d’interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="d26ab-111">When working from the command line, you can use the Tlbimp utility to manually create interop assemblies.</span></span>  
  
### <a name="to-add-references-to-com-objects"></a><span data-ttu-id="d26ab-112">Pour ajouter des références à des objets COM</span><span class="sxs-lookup"><span data-stu-id="d26ab-112">To add references to COM objects</span></span>  
  
1. <span data-ttu-id="d26ab-113">Dans le menu **projet** , choisissez **Ajouter une référence** , puis cliquez sur l’onglet **com** dans la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="d26ab-113">On the **Project** menu, choose **Add Reference** and then click the **COM** tab in the dialog box.</span></span>  
  
2. <span data-ttu-id="d26ab-114">Sélectionnez le composant que vous souhaitez utiliser dans la liste des objets COM.</span><span class="sxs-lookup"><span data-stu-id="d26ab-114">Select the component you want to use from the list of COM objects.</span></span>  
  
3. <span data-ttu-id="d26ab-115">Pour simplifier l’accès à l’assembly d’interopérabilité, ajoutez une `Imports` instruction au début de la classe ou du module dans lequel vous allez utiliser l’objet com.</span><span class="sxs-lookup"><span data-stu-id="d26ab-115">To simplify access to the interop assembly, add an `Imports` statement to the top of the class or module in which you will use the COM object.</span></span> <span data-ttu-id="d26ab-116">Par exemple, l’exemple de code suivant importe l’espace `INKEDLib` de noms pour les objets référencés dans la `Microsoft InkEdit Control 1.0` bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="d26ab-116">For example, the following code example imports the namespace `INKEDLib` for objects referenced in the `Microsoft InkEdit Control 1.0` library.</span></span>  
  
     [!code-vb[VbVbalrInterop#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#40)]  
  
### <a name="to-create-an-interop-assembly-using-tlbimp"></a><span data-ttu-id="d26ab-117">Pour créer un assembly d’interopérabilité à l’aide de Tlbimp</span><span class="sxs-lookup"><span data-stu-id="d26ab-117">To create an interop assembly using Tlbimp</span></span>  
  
1. <span data-ttu-id="d26ab-118">Ajoutez l’emplacement de Tlbimp au chemin de recherche, s’il ne fait pas déjà partie du chemin de recherche et que vous n’êtes pas actuellement dans le répertoire où il se trouve.</span><span class="sxs-lookup"><span data-stu-id="d26ab-118">Add the location of Tlbimp to the search path, if it is not already part of the search path and you are not currently in the directory where it is located.</span></span>  
  
2. <span data-ttu-id="d26ab-119">Appelez Tlbimp à partir d’une invite de commandes, en fournissant les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="d26ab-119">Call Tlbimp from a command prompt, providing the following information:</span></span>  
  
    - <span data-ttu-id="d26ab-120">Nom et emplacement de la DLL qui contient la bibliothèque de types</span><span class="sxs-lookup"><span data-stu-id="d26ab-120">Name and location of the DLL that contains the type library</span></span>  
  
    - <span data-ttu-id="d26ab-121">Nom et emplacement de l’espace de noms où les informations doivent être placées</span><span class="sxs-lookup"><span data-stu-id="d26ab-121">Name and location of the namespace where the information should be placed</span></span>  
  
    - <span data-ttu-id="d26ab-122">Nom et emplacement de l’assembly d’interopérabilité cible</span><span class="sxs-lookup"><span data-stu-id="d26ab-122">Name and location of the target interop assembly</span></span>  
  
     <span data-ttu-id="d26ab-123">Le code suivant est fourni à titre d'exemple :</span><span class="sxs-lookup"><span data-stu-id="d26ab-123">The following code provides an example:</span></span>  
  
    ```console  
    Tlbimp test3.dll /out:NameSpace1 /out:Interop1.dll  
    ```  
  
     <span data-ttu-id="d26ab-124">Vous pouvez utiliser Tlbimp pour créer des assemblys d’interopérabilité pour les bibliothèques de types, même pour les objets COM non inscrits.</span><span class="sxs-lookup"><span data-stu-id="d26ab-124">You can use Tlbimp to create interop assemblies for type libraries, even for unregistered COM objects.</span></span> <span data-ttu-id="d26ab-125">Toutefois, les objets COM référencés par les assemblys d’interopérabilité doivent être correctement inscrits sur l’ordinateur sur lequel ils doivent être utilisés.</span><span class="sxs-lookup"><span data-stu-id="d26ab-125">However, the COM objects referred to by interop assemblies must be properly registered on the computer where they are to be used.</span></span> <span data-ttu-id="d26ab-126">Vous pouvez inscrire un objet COM à l’aide de l’utilitaire regsvr32 inclus dans le système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="d26ab-126">You can register a COM object by using the Regsvr32 utility included with the Windows operating system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d26ab-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d26ab-127">See also</span></span>

- [<span data-ttu-id="d26ab-128">COM Interop</span><span class="sxs-lookup"><span data-stu-id="d26ab-128">COM Interop</span></span>](index.md)
- [<span data-ttu-id="d26ab-129">Tlbimp. exe (importateur de bibliothèques de types)</span><span class="sxs-lookup"><span data-stu-id="d26ab-129">Tlbimp.exe (Type Library Importer)</span></span>](../../../framework/tools/tlbimp-exe-type-library-importer.md)
- [<span data-ttu-id="d26ab-130">Tlbexp. exe (exportateur de bibliothèques de types)</span><span class="sxs-lookup"><span data-stu-id="d26ab-130">Tlbexp.exe (Type Library Exporter)</span></span>](../../../framework/tools/tlbexp-exe-type-library-exporter.md)
- [<span data-ttu-id="d26ab-131">Procédure pas à pas : Implémentation de l’héritage avec les objets COM</span><span class="sxs-lookup"><span data-stu-id="d26ab-131">Walkthrough: Implementing Inheritance with COM Objects</span></span>](walkthrough-implementing-inheritance-with-com-objects.md)
- [<span data-ttu-id="d26ab-132">Dépannage de l’interopérabilité</span><span class="sxs-lookup"><span data-stu-id="d26ab-132">Troubleshooting Interoperability</span></span>](troubleshooting-interoperability.md)
- [<span data-ttu-id="d26ab-133">Imports, instruction (espace de noms et type .NET)</span><span class="sxs-lookup"><span data-stu-id="d26ab-133">Imports Statement (.NET Namespace and Type)</span></span>](../../language-reference/statements/imports-statement-net-namespace-and-type.md)
