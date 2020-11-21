---
title: Guide pratique pour initialiser un dictionnaire avec un initialiseur de collection - Guide de programmation C#
description: Découvrez comment initialiser un dictionnaire en C#, à l’aide de la méthode Add ou d’un initialiseur d’index. Cet exemple montre les deux options.
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.topic: how-to
ms.custom: contperfq2
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: 667b39076f01ab59eb64cf31d7c1dbb921500135
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099338"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a><span data-ttu-id="2aac5-104">Guide pratique pour initialiser un dictionnaire avec un initialiseur de collection (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="2aac5-104">How to initialize a dictionary with a collection initializer (C# Programming Guide)</span></span>

<span data-ttu-id="2aac5-105">Un <xref:System.Collections.Generic.Dictionary%602> contient une collection de paires clé/valeur.</span><span class="sxs-lookup"><span data-stu-id="2aac5-105">A <xref:System.Collections.Generic.Dictionary%602> contains a collection of key/value pairs.</span></span> <span data-ttu-id="2aac5-106">Sa méthode <xref:System.Collections.Generic.Dictionary%602.Add%2A> prend deux paramètres, un pour la clé et un pour la valeur.</span><span class="sxs-lookup"><span data-stu-id="2aac5-106">Its <xref:System.Collections.Generic.Dictionary%602.Add%2A> method takes two parameters, one for the key and one for the value.</span></span> <span data-ttu-id="2aac5-107">Une façon d’initialiser un <xref:System.Collections.Generic.Dictionary%602> ou toute collection dont la méthode `Add` prend plusieurs paramètres consiste à mettre chaque jeu de paramètres entre accolades, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="2aac5-107">One way to initialize a <xref:System.Collections.Generic.Dictionary%602>, or any collection whose `Add` method takes multiple parameters, is to enclose each set of parameters in braces as shown in the following example.</span></span> <span data-ttu-id="2aac5-108">Une autre option consiste à utiliser un initialiseur d’index, également illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="2aac5-108">Another option is to use an index initializer, also shown in the following example.</span></span>

## <a name="example"></a><span data-ttu-id="2aac5-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="2aac5-109">Example</span></span>

<span data-ttu-id="2aac5-110">Dans l’exemple de code suivant, un <xref:System.Collections.Generic.Dictionary%602> est initialisé avec des instances de type `StudentName`.</span><span class="sxs-lookup"><span data-stu-id="2aac5-110">In the following code example, a <xref:System.Collections.Generic.Dictionary%602> is initialized with instances of type `StudentName`.</span></span>  <span data-ttu-id="2aac5-111">La première initialisation utilise la méthode `Add` avec deux arguments.</span><span class="sxs-lookup"><span data-stu-id="2aac5-111">The first initialization uses the `Add` method with two arguments.</span></span> <span data-ttu-id="2aac5-112">Le compilateur génère un appel à `Add` pour chacune des paires de clés `int` et de valeurs `StudentName`.</span><span class="sxs-lookup"><span data-stu-id="2aac5-112">The compiler generates a call to `Add` for each of the pairs of `int` keys and `StudentName` values.</span></span> <span data-ttu-id="2aac5-113">Le deuxième utilise une méthode d’indexeur publique en lecture/écriture de la classe `Dictionary` :</span><span class="sxs-lookup"><span data-stu-id="2aac5-113">The second uses a public read / write indexer method of the `Dictionary` class:</span></span>

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

<span data-ttu-id="2aac5-114">Notez les deux paires d’accolades dans chaque élément de la collection dans la première déclaration.</span><span class="sxs-lookup"><span data-stu-id="2aac5-114">Note the two pairs of braces in each element of the collection in the first declaration.</span></span> <span data-ttu-id="2aac5-115">Les accolades les plus à l’intérieur encadrent l’initialiseur d’objet pour le `StudentName` , et les accolades les plus extérieures encadrent l’initialiseur pour la paire clé/valeur qui sera ajoutée à `students` <xref:System.Collections.Generic.Dictionary%602> .</span><span class="sxs-lookup"><span data-stu-id="2aac5-115">The innermost braces enclose the object initializer for the `StudentName`, and the outermost braces enclose the initializer for the key/value pair that will be added to the `students` <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="2aac5-116">Pour finir, l’initialiseur de collection entier pour le dictionnaire est placé entre accolades.</span><span class="sxs-lookup"><span data-stu-id="2aac5-116">Finally, the whole collection initializer for the dictionary is enclosed in braces.</span></span> <span data-ttu-id="2aac5-117">Dans la deuxième initialisation, le côté gauche de l’affectation est la clé et le côté droit est la valeur, avec un initialiseur d’objet pour `StudentName`.</span><span class="sxs-lookup"><span data-stu-id="2aac5-117">In the second initialization, the left side of the assignment is the key and the right side is the value, using an object initializer for `StudentName`.</span></span>

## <a name="see-also"></a><span data-ttu-id="2aac5-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2aac5-118">See also</span></span>

- [<span data-ttu-id="2aac5-119">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="2aac5-119">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2aac5-120">Initialiseurs d’objets et de collections</span><span class="sxs-lookup"><span data-stu-id="2aac5-120">Object and Collection Initializers</span></span>](./object-and-collection-initializers.md)
