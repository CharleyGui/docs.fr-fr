---
title: Création de nouvelles chaînes dans .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CopyTo method
- Join method
- Format method
- Concat method
- strings [.NET Framework], creating
- Insert method
ms.assetid: 06fdf123-2fac-4459-8904-eb48ab908a30
ms.openlocfilehash: ef65c50111d6ba91ab70d0b9c8cb90c606f9366c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73103817"
---
# <a name="creating-new-strings-in-net"></a><span data-ttu-id="00ff3-102">Création de nouvelles chaînes dans .NET</span><span class="sxs-lookup"><span data-stu-id="00ff3-102">Creating New Strings in .NET</span></span>
<span data-ttu-id="00ff3-103">Le .NET Framework permet de créer des chaînes à l’aide d’une assignation simple, et surcharge un constructeur de classe pour prendre en charge la création de chaînes à l’aide de plusieurs paramètres différents.</span><span class="sxs-lookup"><span data-stu-id="00ff3-103">The .NET Framework allows strings to be created using simple assignment, and also overloads a class constructor to support string creation using a number of different parameters.</span></span> <span data-ttu-id="00ff3-104">Le .NET Framework fournit également plusieurs méthodes dans la classe <xref:System.String?displayProperty=nameWithType> qui créent des objets de chaînes en combinant plusieurs chaînes, tableaux de chaînes ou objets.</span><span class="sxs-lookup"><span data-stu-id="00ff3-104">The .NET Framework also provides several methods in the <xref:System.String?displayProperty=nameWithType> class that create new string objects by combining several strings, arrays of strings, or objects.</span></span>  
  
## <a name="creating-strings-using-assignment"></a><span data-ttu-id="00ff3-105">Création de chaînes à l’aide d’une affectation</span><span class="sxs-lookup"><span data-stu-id="00ff3-105">Creating Strings Using Assignment</span></span>  
 <span data-ttu-id="00ff3-106">Le moyen le plus simple de créer un objet <xref:System.String> consiste à assigner un littéral de chaîne à un objet <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="00ff3-106">The easiest way to create a new <xref:System.String> object is simply to assign a string literal to a <xref:System.String> object.</span></span>  
  
## <a name="creating-strings-using-a-class-constructor"></a><span data-ttu-id="00ff3-107">Création de chaînes à l’aide d’un constructeur de classe</span><span class="sxs-lookup"><span data-stu-id="00ff3-107">Creating Strings Using a Class Constructor</span></span>  
 <span data-ttu-id="00ff3-108">Vous pouvez utiliser des surcharges du constructeur de classe <xref:System.String> pour créer des chaînes à partir de tableaux de caractères.</span><span class="sxs-lookup"><span data-stu-id="00ff3-108">You can use overloads of the <xref:System.String> class constructor to create strings from character arrays.</span></span> <span data-ttu-id="00ff3-109">Vous pouvez également créer une chaîne en dupliquant un caractère spécifique un nombre spécifié de fois.</span><span class="sxs-lookup"><span data-stu-id="00ff3-109">You can also create a new string by duplicating a particular character a specified number of times.</span></span>  
  
## <a name="methods-that-return-strings"></a><span data-ttu-id="00ff3-110">Méthodes retournant des chaînes</span><span class="sxs-lookup"><span data-stu-id="00ff3-110">Methods that Return Strings</span></span>  
 <span data-ttu-id="00ff3-111">Le tableau suivant présente plusieurs méthodes utiles qui retournent de nouveaux objets String.</span><span class="sxs-lookup"><span data-stu-id="00ff3-111">The following table lists several useful methods that return new string objects.</span></span>  
  
|<span data-ttu-id="00ff3-112">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="00ff3-112">Method name</span></span>|<span data-ttu-id="00ff3-113">Utilisation</span><span class="sxs-lookup"><span data-stu-id="00ff3-113">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Format%2A?displayProperty=nameWithType>|<span data-ttu-id="00ff3-114">Génère une chaîne mise en forme à partir d’un ensemble d’objets en entrée.</span><span class="sxs-lookup"><span data-stu-id="00ff3-114">Builds a formatted string from a set of input objects.</span></span>|  
|<xref:System.String.Concat%2A?displayProperty=nameWithType>|<span data-ttu-id="00ff3-115">Génère des chaînes à partir de deux ou de plusieurs chaînes.</span><span class="sxs-lookup"><span data-stu-id="00ff3-115">Builds strings from two or more strings.</span></span>|  
|<xref:System.String.Join%2A?displayProperty=nameWithType>|<span data-ttu-id="00ff3-116">Génère une nouvelle chaîne en combinant un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="00ff3-116">Builds a new string by combining an array of strings.</span></span>|  
|<xref:System.String.Insert%2A?displayProperty=nameWithType>|<span data-ttu-id="00ff3-117">Génère une nouvelle chaîne en insérant une chaîne dans l’index spécifié d’une chaîne existante.</span><span class="sxs-lookup"><span data-stu-id="00ff3-117">Builds a new string by inserting a string into the specified index of an existing string.</span></span>|  
|<xref:System.String.CopyTo%2A?displayProperty=nameWithType>|<span data-ttu-id="00ff3-118">Copie des caractères spécifiés dans une chaîne à une position spécifiée dans un tableau de caractères.</span><span class="sxs-lookup"><span data-stu-id="00ff3-118">Copies specified characters in a string into a specified position in an array of characters.</span></span>|  
  
### <a name="format"></a><span data-ttu-id="00ff3-119">Format</span><span class="sxs-lookup"><span data-stu-id="00ff3-119">Format</span></span>  
 <span data-ttu-id="00ff3-120">Vous pouvez utiliser la méthode **String.Format** pour créer des chaînes mises en forme et concaténer des chaînes représentant plusieurs objets.</span><span class="sxs-lookup"><span data-stu-id="00ff3-120">You can use the **String.Format** method to create formatted strings and concatenate strings representing multiple objects.</span></span> <span data-ttu-id="00ff3-121">Cette méthode convertit automatiquement tout objet passé en une chaîne.</span><span class="sxs-lookup"><span data-stu-id="00ff3-121">This method automatically converts any passed object into a string.</span></span> <span data-ttu-id="00ff3-122">Par exemple, si votre application doit afficher une valeur **Int32** et une valeur **DateTime** à l’utilisateur, vous pouvez aisément construire une chaîne représentant ces valeurs à l’aide de la méthode **Format**.</span><span class="sxs-lookup"><span data-stu-id="00ff3-122">For example, if your application must display an **Int32** value and a **DateTime** value to the user, you can easily construct a string to represent these values using the **Format** method.</span></span> <span data-ttu-id="00ff3-123">Pour plus d’informations sur les conventions de mise en forme utilisées avec cette méthode, consultez la section relative à la [mise en forme composite](../../../docs/standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="00ff3-123">For information about formatting conventions used with this method, see the section on [composite formatting](../../../docs/standard/base-types/composite-formatting.md).</span></span>  
  
 <span data-ttu-id="00ff3-124">L’exemple suivant utilise la méthode **Format** pour créer une chaîne utilisant une variable de type integer.</span><span class="sxs-lookup"><span data-stu-id="00ff3-124">The following example uses the **Format** method to create a string that uses an integer variable.</span></span>  
  
 [!code-csharp[Strings.Creating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#1)]
 [!code-vb[Strings.Creating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#1)]  
  
 <span data-ttu-id="00ff3-125">Dans cet exemple, <xref:System.DateTime.Now%2A?displayProperty=nameWithType> affiche la date et l’heure actuelles de la manière spécifiée par la culture associée au thread actuel.</span><span class="sxs-lookup"><span data-stu-id="00ff3-125">In this example,<xref:System.DateTime.Now%2A?displayProperty=nameWithType> displays the current date and time in a manner specified by the culture associated with the current thread.</span></span>  
  
### <a name="concat"></a><span data-ttu-id="00ff3-126">Concat</span><span class="sxs-lookup"><span data-stu-id="00ff3-126">Concat</span></span>  
 <span data-ttu-id="00ff3-127">La méthode **String.Concat** peut être utilisée pour créer facilement un objet chaîne à partir de deux ou de plusieurs objets existants.</span><span class="sxs-lookup"><span data-stu-id="00ff3-127">The **String.Concat** method can be used to easily create a new string object from two or more existing objects.</span></span> <span data-ttu-id="00ff3-128">Elle offre un moyen de concaténer des chaînes indépendamment du langage.</span><span class="sxs-lookup"><span data-stu-id="00ff3-128">It provides a language-independent way to concatenate strings.</span></span> <span data-ttu-id="00ff3-129">Cette méthode accepte toute classe qui dérive de **System.Object**.</span><span class="sxs-lookup"><span data-stu-id="00ff3-129">This method accepts any class that derives from **System.Object**.</span></span> <span data-ttu-id="00ff3-130">L’exemple suivant crée une chaîne à partir de deux objets String existants et d’un caractère à utiliser comme séparateur.</span><span class="sxs-lookup"><span data-stu-id="00ff3-130">The following example creates a string from two existing string objects and a separating character.</span></span>  
  
 [!code-csharp[Strings.Creating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#2)]
 [!code-vb[Strings.Creating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#2)]  
  
### <a name="join"></a><span data-ttu-id="00ff3-131">Join</span><span class="sxs-lookup"><span data-stu-id="00ff3-131">Join</span></span>  
 <span data-ttu-id="00ff3-132">La méthode **String.Join** crée une chaîne à partir d’un tableau de chaînes et d’une chaîne de séparation.</span><span class="sxs-lookup"><span data-stu-id="00ff3-132">The **String.Join** method creates a new string from an array of strings and a separator string.</span></span> <span data-ttu-id="00ff3-133">Cette méthode est utile si vous voulez concaténer plusieurs chaînes et en faire une liste éventuellement séparée par une virgule.</span><span class="sxs-lookup"><span data-stu-id="00ff3-133">This method is useful if you want to concatenate multiple strings together, making a list perhaps separated by a comma.</span></span>  
  
 <span data-ttu-id="00ff3-134">L’exemple suivant utilise un espace pour lier un tableau de chaînes.</span><span class="sxs-lookup"><span data-stu-id="00ff3-134">The following example uses a space to bind a string array.</span></span>  
  
 [!code-csharp[Strings.Creating#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#3)]
 [!code-vb[Strings.Creating#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#3)]  
  
### <a name="insert"></a><span data-ttu-id="00ff3-135">Insérer</span><span class="sxs-lookup"><span data-stu-id="00ff3-135">Insert</span></span>  
 <span data-ttu-id="00ff3-136">La méthode **String.Insert** crée une chaîne en insérant une chaîne à une position spécifiée dans une autre chaîne.</span><span class="sxs-lookup"><span data-stu-id="00ff3-136">The **String.Insert** method creates a new string by inserting a string into a specified position in another string.</span></span> <span data-ttu-id="00ff3-137">Cette méthode utilise un index de base zéro.</span><span class="sxs-lookup"><span data-stu-id="00ff3-137">This method uses a zero-based index.</span></span> <span data-ttu-id="00ff3-138">L’exemple suivant insère une chaîne à la cinquième position d’index de `MyString` et crée une chaîne avec cette valeur.</span><span class="sxs-lookup"><span data-stu-id="00ff3-138">The following example inserts a string into the fifth index position of `MyString` and creates a new string with this value.</span></span>  
  
 [!code-csharp[Strings.Creating#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#4)]
 [!code-vb[Strings.Creating#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#4)]  
  
### <a name="copyto"></a><span data-ttu-id="00ff3-139">CopyTo</span><span class="sxs-lookup"><span data-stu-id="00ff3-139">CopyTo</span></span>  
 <span data-ttu-id="00ff3-140">La méthode **String.CopyTo** copie des fragments d’une chaîne dans un tableau de caractères.</span><span class="sxs-lookup"><span data-stu-id="00ff3-140">The **String.CopyTo** method copies portions of a string into an array of characters.</span></span> <span data-ttu-id="00ff3-141">Vous pouvez spécifier l’index de début de la chaîne et le nombre de caractères à copier.</span><span class="sxs-lookup"><span data-stu-id="00ff3-141">You can specify both the beginning index of the string and the number of characters to be copied.</span></span> <span data-ttu-id="00ff3-142">Cette méthode utilise l’index source, un tableau de caractères, l’index de destination et le nombre de caractères à copier.</span><span class="sxs-lookup"><span data-stu-id="00ff3-142">This method takes the source index, an array of characters, the destination index, and the number of characters to copy.</span></span> <span data-ttu-id="00ff3-143">Tous les index sont de base zéro.</span><span class="sxs-lookup"><span data-stu-id="00ff3-143">All indexes are zero-based.</span></span>  
  
 <span data-ttu-id="00ff3-144">L’exemple suivant utilise la méthode **CopyTo** pour copier les caractères du mot « Hello » d’un objet String vers la première position d’un tableau de caractères.</span><span class="sxs-lookup"><span data-stu-id="00ff3-144">The following example uses the **CopyTo** method to copy the characters of the word "Hello" from a string object to the first index position of an array of characters.</span></span>  
  
 [!code-csharp[Strings.Creating#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Strings.Creating/cs/Example.cs#5)]
 [!code-vb[Strings.Creating#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Strings.Creating/vb/Example.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="00ff3-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00ff3-145">See also</span></span>

- [<span data-ttu-id="00ff3-146">Opérations de base des cordes</span><span class="sxs-lookup"><span data-stu-id="00ff3-146">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
- [<span data-ttu-id="00ff3-147">Mise en forme composite</span><span class="sxs-lookup"><span data-stu-id="00ff3-147">Composite Formatting</span></span>](../../../docs/standard/base-types/composite-formatting.md)
