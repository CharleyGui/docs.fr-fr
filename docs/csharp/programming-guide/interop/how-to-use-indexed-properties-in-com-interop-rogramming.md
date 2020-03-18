---
title: Comment utiliser les propriétés indexées dans la programmation interop COM - Guide de programmation C
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: 864e2274f0e0e79b4843e0bb67b5c4384eac8588
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712063"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a><span data-ttu-id="f3e31-102">Comment utiliser les propriétés indexées dans la programmation interop COM (Guide de programmation C)</span><span class="sxs-lookup"><span data-stu-id="f3e31-102">How to use indexed properties in COM interop programming (C# Programming Guide)</span></span>
<span data-ttu-id="f3e31-103">Les *propriétés indexées* améliorent la façon dont les propriétés COM avec des paramètres sont consommées dans la programmation C#.</span><span class="sxs-lookup"><span data-stu-id="f3e31-103">*Indexed properties* improve the way in which COM properties that have parameters are consumed in C# programming.</span></span> <span data-ttu-id="f3e31-104">Les propriétés indexées fonctionnent avec d’autres fonctionnalités dans Visual C#, comme les [arguments nommés et facultatifs](../classes-and-structs/named-and-optional-arguments.md), un nouveau type ([dynamique](../../language-reference/builtin-types/reference-types.md)) et [les informations de type incorporées](../../../standard/assembly/embed-types-visual-studio.md), pour améliorer la programmation Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="f3e31-104">Indexed properties work together with other features in Visual C#, such as [named and optional arguments](../classes-and-structs/named-and-optional-arguments.md), a new type ([dynamic](../../language-reference/builtin-types/reference-types.md)), and [embedded type information](../../../standard/assembly/embed-types-visual-studio.md), to enhance Microsoft Office programming.</span></span>  
  
 <span data-ttu-id="f3e31-105">Dans les versions antérieures de C#, les méthodes sont accessibles comme des propriétés uniquement si la méthode `get` n’a aucun paramètre et que la méthode `set` a un seul et unique paramètre de valeur.</span><span class="sxs-lookup"><span data-stu-id="f3e31-105">In earlier versions of C#, methods are accessible as properties only if the `get` method has no parameters and the `set` method has one and only one value parameter.</span></span> <span data-ttu-id="f3e31-106">Toutefois, toutes les propriétés COM ne respectent pas ces restrictions.</span><span class="sxs-lookup"><span data-stu-id="f3e31-106">However, not all COM properties meet those restrictions.</span></span> <span data-ttu-id="f3e31-107">Par exemple, la propriété <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> d’Excel a un accesseur `get`, qui nécessite un paramètre pour le nom de la plage.</span><span class="sxs-lookup"><span data-stu-id="f3e31-107">For example, the Excel <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> property has a `get` accessor that requires a parameter for the name of the range.</span></span> <span data-ttu-id="f3e31-108">Dans le passé, parce que vous ne pouviez pas accéder à la propriété `Range` directement, vous deviez utiliser la méthode `get_Range` à la place, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="f3e31-108">In the past, because you could not access the `Range` property directly, you had to use the `get_Range` method instead, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 <span data-ttu-id="f3e31-109">Les propriétés indexées vous permettent d’écrire ce qui suit à la place :</span><span class="sxs-lookup"><span data-stu-id="f3e31-109">Indexed properties enable you to write the following instead:</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
> <span data-ttu-id="f3e31-110">L’exemple précédent utilise également la fonctionnalité des [arguments facultatifs](../classes-and-structs/named-and-optional-arguments.md), qui vous permet d’omettre `Type.Missing`.</span><span class="sxs-lookup"><span data-stu-id="f3e31-110">The previous example also uses the [optional arguments](../classes-and-structs/named-and-optional-arguments.md) feature, which enables you to omit `Type.Missing`.</span></span>  
  
 <span data-ttu-id="f3e31-111">De même, pour définir la valeur de la propriété `Value` d’un objet <xref:Microsoft.Office.Interop.Excel.Range> dans C# 3.0 et les versions antérieures, deux arguments sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="f3e31-111">Similarly to set the value of the `Value` property of a <xref:Microsoft.Office.Interop.Excel.Range> object in C# 3.0 and earlier, two arguments are required.</span></span> <span data-ttu-id="f3e31-112">L’un fournit un argument pour un paramètre facultatif qui spécifie le type de la valeur de la plage.</span><span class="sxs-lookup"><span data-stu-id="f3e31-112">One supplies an argument for an optional parameter that specifies the type of the range value.</span></span> <span data-ttu-id="f3e31-113">L’autre fournit la valeur de la propriété `Value`.</span><span class="sxs-lookup"><span data-stu-id="f3e31-113">The other supplies the value for the `Value` property.</span></span> <span data-ttu-id="f3e31-114">Les exemples suivants illustrent ces techniques.</span><span class="sxs-lookup"><span data-stu-id="f3e31-114">The following examples illustrate these techniques.</span></span> <span data-ttu-id="f3e31-115">Les deux définissent la valeur de la cellule A1 sur `Name`.</span><span class="sxs-lookup"><span data-stu-id="f3e31-115">Both set the value of the A1 cell to `Name`.</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 <span data-ttu-id="f3e31-116">Les propriétés indexées vous permettent d’écrire le code suivant à la place.</span><span class="sxs-lookup"><span data-stu-id="f3e31-116">Indexed properties enable you to write the following code instead.</span></span>  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 <span data-ttu-id="f3e31-117">Vous ne pouvez pas créer vos propres propriétés indexées.</span><span class="sxs-lookup"><span data-stu-id="f3e31-117">You cannot create indexed properties of your own.</span></span> <span data-ttu-id="f3e31-118">La fonctionnalité prend uniquement en charge la consommation de propriétés indexées existantes.</span><span class="sxs-lookup"><span data-stu-id="f3e31-118">The feature only supports consumption of existing indexed properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3e31-119"> Exemple</span><span class="sxs-lookup"><span data-stu-id="f3e31-119">Example</span></span>  
 <span data-ttu-id="f3e31-120">L'exemple de code suivant illustre l'exemple complet.</span><span class="sxs-lookup"><span data-stu-id="f3e31-120">The following code shows a complete example.</span></span> <span data-ttu-id="f3e31-121">Pour plus d’informations sur la façon de mettre en place un projet qui accède à l’API Office, voir [Comment accéder aux objets Interop Office en utilisant les fonctionnalités C](./how-to-access-office-onterop-objects.md).</span><span class="sxs-lookup"><span data-stu-id="f3e31-121">For more information about how to set up a project that accesses the Office API, see [How to access Office interop objects by using C# features](./how-to-access-office-onterop-objects.md).</span></span>
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a><span data-ttu-id="f3e31-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3e31-122">See also</span></span>

- [<span data-ttu-id="f3e31-123">Arguments nommés et facultatifs</span><span class="sxs-lookup"><span data-stu-id="f3e31-123">Named and Optional Arguments</span></span>](../classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="f3e31-124">Dynamique</span><span class="sxs-lookup"><span data-stu-id="f3e31-124">dynamic</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="f3e31-125">Utilisation du type dynamic</span><span class="sxs-lookup"><span data-stu-id="f3e31-125">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="f3e31-126">Comment utiliser les arguments nommés et facultatifs dans la programmation du Bureau</span><span class="sxs-lookup"><span data-stu-id="f3e31-126">How to use named and optional arguments in Office programming</span></span>](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [<span data-ttu-id="f3e31-127">Comment accéder aux objets Office Interop à l’aide des fonctionnalités C#</span><span class="sxs-lookup"><span data-stu-id="f3e31-127">How to access Office interop objects by using C# features</span></span>](./how-to-access-office-onterop-objects.md)
- [<span data-ttu-id="f3e31-128">Procédure pas à pas : programmation Office</span><span class="sxs-lookup"><span data-stu-id="f3e31-128">Walkthrough: Office Programming</span></span>](./walkthrough-office-programming.md)
