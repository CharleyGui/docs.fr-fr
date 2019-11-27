---
title: Conversions de type
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- changing data types [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 1cdacd21-ba31-4b62-b5be-395e41eeaa17
ms.openlocfilehash: fbf0c9877cf9a9b4364c8c058c61e847ad7bf049
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348720"
---
# <a name="type-conversions-in-visual-basic"></a><span data-ttu-id="d8fb8-102">Conversions de type en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d8fb8-102">Type Conversions in Visual Basic</span></span>
<span data-ttu-id="d8fb8-103">Le processus de modification d’une valeur d’un type de données en un autre type est appelé *conversion*.</span><span class="sxs-lookup"><span data-stu-id="d8fb8-103">The process of changing a value from one data type to another type is called *conversion*.</span></span> <span data-ttu-id="d8fb8-104">Les conversions sont *étendues* ou *restrictives*, en fonction des capacités de données des types impliqués.</span><span class="sxs-lookup"><span data-stu-id="d8fb8-104">Conversions are either *widening* or *narrowing*, depending on the data capacities of the types involved.</span></span> <span data-ttu-id="d8fb8-105">Ils sont également *implicites* ou *explicites*, selon la syntaxe du code source.</span><span class="sxs-lookup"><span data-stu-id="d8fb8-105">They are also *implicit* or *explicit*, depending on the syntax in the source code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d8fb8-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d8fb8-106">In This Section</span></span>  
 [<span data-ttu-id="d8fb8-107">Conversions étendues et restrictives</span><span class="sxs-lookup"><span data-stu-id="d8fb8-107">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 <span data-ttu-id="d8fb8-108">Explique les conversions classifiées selon que le type de destination peut contenir les données.</span><span class="sxs-lookup"><span data-stu-id="d8fb8-108">Explains conversions classified by whether the destination type can hold the data.</span></span>  
  
 [<span data-ttu-id="d8fb8-109">Conversions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="d8fb8-109">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 <span data-ttu-id="d8fb8-110">Décrit les conversions classifiées selon que Visual Basic les effectue automatiquement.</span><span class="sxs-lookup"><span data-stu-id="d8fb8-110">Discusses conversions classified by whether Visual Basic performs them automatically.</span></span>  
  
 [<span data-ttu-id="d8fb8-111">Conversion entre des chaînes et d’autres types</span><span class="sxs-lookup"><span data-stu-id="d8fb8-111">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 <span data-ttu-id="d8fb8-112">Illustre la conversion entre des chaînes et des valeurs numériques, `Boolean`ou de date/heure.</span><span class="sxs-lookup"><span data-stu-id="d8fb8-112">Illustrates converting between strings and numeric, `Boolean`, or date/time values.</span></span>  
  
 [<span data-ttu-id="d8fb8-113">Comment : convertir un objet en un autre type dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d8fb8-113">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 <span data-ttu-id="d8fb8-114">Montre comment convertir une variable `Object` en un autre type de données.</span><span class="sxs-lookup"><span data-stu-id="d8fb8-114">Shows how to convert an `Object` variable to any other data type.</span></span>  
  
 [<span data-ttu-id="d8fb8-115">Conversions de tableau</span><span class="sxs-lookup"><span data-stu-id="d8fb8-115">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 <span data-ttu-id="d8fb8-116">Vous guide tout au long du processus de conversion entre des tableaux de types de données différents.</span><span class="sxs-lookup"><span data-stu-id="d8fb8-116">Steps you through the process of converting between arrays of different data types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d8fb8-117">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="d8fb8-117">Related Sections</span></span>  
 [<span data-ttu-id="d8fb8-118">Types de données</span><span class="sxs-lookup"><span data-stu-id="d8fb8-118">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 <span data-ttu-id="d8fb8-119">Présente les types de données Visual Basic et décrit comment les utiliser.</span><span class="sxs-lookup"><span data-stu-id="d8fb8-119">Introduces the Visual Basic data types and describes how to use them.</span></span>  
  
 [<span data-ttu-id="d8fb8-120">Types de données</span><span class="sxs-lookup"><span data-stu-id="d8fb8-120">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)  
 <span data-ttu-id="d8fb8-121">Répertorie les types de données élémentaires fournis par Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d8fb8-121">Lists the elementary data types supplied by Visual Basic.</span></span>  
  
 [<span data-ttu-id="d8fb8-122">Dépannage des types de données</span><span class="sxs-lookup"><span data-stu-id="d8fb8-122">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 <span data-ttu-id="d8fb8-123">Décrit certains problèmes courants qui peuvent survenir lors de l’utilisation de types de données.</span><span class="sxs-lookup"><span data-stu-id="d8fb8-123">Discusses some common problems that can arise when working with data types.</span></span>
