---
title: Transformations fonctionnelles pures de données XML
ms.date: 07/20/2015
ms.assetid: 5e19b74a-7773-4b58-b110-953ffd364c55
ms.openlocfilehash: 60ec6a5f9c643ea5cc0511f48356d6bfa3ad5748
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396322"
---
# <a name="pure-functional-transformations-of-xml-visual-basic"></a><span data-ttu-id="daddb-102">Transformations fonctionnelles pures de XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="daddb-102">Pure Functional Transformations of XML (Visual Basic)</span></span>
<span data-ttu-id="daddb-103">Cette section fournit un didacticiel sur les transformations fonctionnelles de données XML.</span><span class="sxs-lookup"><span data-stu-id="daddb-103">This section provides a functional transformation tutorial for XML.</span></span> <span data-ttu-id="daddb-104">Elle contient des explications des principaux concepts et constructions que vous devez comprendre pour utiliser des transformations fonctionnelles, ainsi que des exemples d'utilisation de transformations fonctionnelles pour manipuler un document XML.</span><span class="sxs-lookup"><span data-stu-id="daddb-104">This includes explanations of the main concepts and language constructs that you must understand to use functional transformations, and examples of using functional transformations to manipulate an XML document.</span></span> <span data-ttu-id="daddb-105">Bien que ce didacticiel contienne des exemples de code LINQ to XML, tous les concepts sous-jacents s'appliquent également à d'autres technologies LINQ.</span><span class="sxs-lookup"><span data-stu-id="daddb-105">Although this tutorial provides LINQ to XML code examples, all of the underlying concepts also apply to other LINQ technologies.</span></span>  
  
 <span data-ttu-id="daddb-106">Le didacticiel [: manipulation de contenu dans un document WordprocessingML (Visual Basic)](tutorial-manipulating-content-in-a-wordprocessingml-document.md) fournit une série d’exemples, chacun basé sur le précédent.</span><span class="sxs-lookup"><span data-stu-id="daddb-106">The [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial provides a series of examples, each building on the previous one.</span></span> <span data-ttu-id="daddb-107">Ces exemples illustrent l'approche transformationnelle fonctionnelle pure de la manipulation de données XML.</span><span class="sxs-lookup"><span data-stu-id="daddb-107">These examples demonstrate the pure functional transformational approach to manipulating XML.</span></span>  
  
 <span data-ttu-id="daddb-108">Ce didacticiel suppose que vous avez des connaissances pratiques sur Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="daddb-108">This tutorial assumes a working knowledge of Visual Basic.</span></span> <span data-ttu-id="daddb-109">Aucune sémantique détaillée des constructions propres au langage n'est fournie dans ce didacticiel, mais des liens sont fournis vers la documentation de langage appropriée.</span><span class="sxs-lookup"><span data-stu-id="daddb-109">Detailed semantics of the language constructs are not provided in this tutorial, but links are provided to the language documentation as appropriate.</span></span>  
  
 <span data-ttu-id="daddb-110">On suppose également que vous avez une connaissance pratique des concepts informatiques de base et du langage XML, y compris les espaces de noms XML.</span><span class="sxs-lookup"><span data-stu-id="daddb-110">A working knowledge of basic computer science concepts and XML, including XML namespaces, is also assumed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="daddb-111">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="daddb-111">In This Section</span></span>  
  
|<span data-ttu-id="daddb-112">Rubrique</span><span class="sxs-lookup"><span data-stu-id="daddb-112">Topic</span></span>|<span data-ttu-id="daddb-113">Description</span><span class="sxs-lookup"><span data-stu-id="daddb-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="daddb-114">Présentation des transformations fonctionnelles pures (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="daddb-114">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](introduction-to-pure-functional-transformations.md)|<span data-ttu-id="daddb-115">Décrit les transformations fonctionnelles et définit la terminologie appropriée.</span><span class="sxs-lookup"><span data-stu-id="daddb-115">Describes functional transformations and defines the relevant terminology.</span></span>|  
|[<span data-ttu-id="daddb-116">Didacticiel : exécution différée (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="daddb-116">Tutorial: Deferred Execution (Visual Basic)</span></span>](tutorial-deferred-execution.md)|<span data-ttu-id="daddb-117">Décrit l'évaluation et l'exécution différées en détail.</span><span class="sxs-lookup"><span data-stu-id="daddb-117">Describes lazy evaluation and deferred execution in detail.</span></span>|  
|[<span data-ttu-id="daddb-118">Didacticiel : manipulation de contenu dans un document WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="daddb-118">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](tutorial-manipulating-content-in-a-wordprocessingml-document.md)|<span data-ttu-id="daddb-119">Didacticiel qui illustre une transformation fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="daddb-119">A tutorial that demonstrates a functional transformation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="daddb-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="daddb-120">See also</span></span>

- [<span data-ttu-id="daddb-121">Interrogation d’arborescences XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="daddb-121">Querying XML Trees (Visual Basic)</span></span>](querying-xml-trees.md)
