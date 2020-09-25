---
title: Procédures stockées
ms.date: 03/30/2017
ms.assetid: 4d23dd7a-a85f-44ff-a717-af7d0950c0fc
ms.openlocfilehash: 57420d95ec27af3b572940202fb6bc288c6888da
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203512"
---
# <a name="stored-procedures"></a><span data-ttu-id="7b6ee-102">Procédures stockées</span><span class="sxs-lookup"><span data-stu-id="7b6ee-102">Stored Procedures</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="7b6ee-103">utilise des méthodes dans votre modèle objet pour représenter des procédures stockées dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="7b6ee-103">uses methods in your object model to represent stored procedures in the database.</span></span> <span data-ttu-id="7b6ee-104">Vous désignez des méthodes comme des procédures stockées en appliquant l'attribut <xref:System.Data.Linq.Mapping.FunctionAttribute> et, si nécessaire, l'attribut <xref:System.Data.Linq.Mapping.ParameterAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7b6ee-104">You designate methods as stored procedures by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="7b6ee-105">Pour plus d’informations, consultez [le modèle objet LINQ to SQL](the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="7b6ee-105">For more information, see [The LINQ to SQL Object Model](the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="7b6ee-106">Les développeurs qui utilisent Visual Studio utilisent généralement le Concepteur Objet Relationnel pour mapper des procédures stockées.</span><span class="sxs-lookup"><span data-stu-id="7b6ee-106">Developers using Visual Studio would typically use the Object Relational Designer to map stored procedures.</span></span> <span data-ttu-id="7b6ee-107">Les rubriques de cette section montrent comment former et appeler ces méthodes dans votre application si vous écrivez vous-même le code.</span><span class="sxs-lookup"><span data-stu-id="7b6ee-107">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7b6ee-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="7b6ee-108">In This Section</span></span>  

 [<span data-ttu-id="7b6ee-109">Procédure : Retourner des ensembles de lignes</span><span class="sxs-lookup"><span data-stu-id="7b6ee-109">How to: Return Rowsets</span></span>](how-to-return-rowsets.md)  
 <span data-ttu-id="7b6ee-110">Décrit comment retourner des lignes de données et comment utiliser un paramètre d'entrée.</span><span class="sxs-lookup"><span data-stu-id="7b6ee-110">Describes how to return rows of data and shows how to use an input parameter.</span></span>  
  
 [<span data-ttu-id="7b6ee-111">Procédure : Utiliser des procédures stockées qui prennent des paramètres</span><span class="sxs-lookup"><span data-stu-id="7b6ee-111">How to: Use Stored Procedures that Take Parameters</span></span>](how-to-use-stored-procedures-that-take-parameters.md)  
 <span data-ttu-id="7b6ee-112">Décrit comment utiliser des paramètres d'entrée et de sortie.</span><span class="sxs-lookup"><span data-stu-id="7b6ee-112">Describes how to use input and output parameters.</span></span>  
  
 [<span data-ttu-id="7b6ee-113">Procédure : Utiliser des procédures stockées mappées pour plusieurs formes de résultats</span><span class="sxs-lookup"><span data-stu-id="7b6ee-113">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)  
 <span data-ttu-id="7b6ee-114">Explique comment permettre le retour de plusieurs formes dans la même procédure stockée.</span><span class="sxs-lookup"><span data-stu-id="7b6ee-114">Describes how to provide for returns of multiple shapes in the same stored procedure.</span></span>  
  
 [<span data-ttu-id="7b6ee-115">Procédure : Utiliser des procédures stockées mappées pour des formes de résultats séquentielles</span><span class="sxs-lookup"><span data-stu-id="7b6ee-115">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)  
 <span data-ttu-id="7b6ee-116">Explique comment permettre plusieurs formes lorsque la séquence de retour est connue.</span><span class="sxs-lookup"><span data-stu-id="7b6ee-116">Describes how to provide for multiple shapes where the return sequence is known.</span></span>  
  
 [<span data-ttu-id="7b6ee-117">Personnalisation d'opérations à l'aide de procédures stockées</span><span class="sxs-lookup"><span data-stu-id="7b6ee-117">Customizing Operations By Using Stored Procedures</span></span>](customizing-operations-by-using-stored-procedures.md)  
 <span data-ttu-id="7b6ee-118">Explique comment utiliser des procédures stockées pour implémenter les opérations d'insertion, de mise à jour et de suppression.</span><span class="sxs-lookup"><span data-stu-id="7b6ee-118">Describes how to use stored procedures to implement insert, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="7b6ee-119">Personnalisation d'opérations à l'aide de procédures stockées uniquement</span><span class="sxs-lookup"><span data-stu-id="7b6ee-119">Customizing Operations by Using Stored Procedures Exclusively</span></span>](customizing-operations-by-using-stored-procedures-exclusively.md)  
 <span data-ttu-id="7b6ee-120">Explique comment utiliser uniquement des procédures stockées pour implémenter les opérations d'insertion, de mise à jour et de suppression.</span><span class="sxs-lookup"><span data-stu-id="7b6ee-120">Describes how to use nothing but stored procedures to implement insert, update, and delete operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7b6ee-121">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="7b6ee-121">Related Sections</span></span>  

 [<span data-ttu-id="7b6ee-122">Guide de programmation</span><span class="sxs-lookup"><span data-stu-id="7b6ee-122">Programming Guide</span></span>](programming-guide.md)  
 <span data-ttu-id="7b6ee-123">Fournit des informations sur la création et l'utilisation de votre modèle objet [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7b6ee-123">Provides information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="7b6ee-124">Procédure pas à pas : Utilisation de procédures stockées uniquement (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b6ee-124">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>](walkthrough-using-only-stored-procedures-visual-basic.md)  
 <span data-ttu-id="7b6ee-125">Inclut des procédures qui expliquent comment utiliser des procédures stockées dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7b6ee-125">Includes procedures that illustrate how to use stored procedures in Visual Basic.</span></span>  
  
 [<span data-ttu-id="7b6ee-126">Procédure pas à pas : Utilisation de procédures stockées uniquement (C#)</span><span class="sxs-lookup"><span data-stu-id="7b6ee-126">Walkthrough: Using Only Stored Procedures (C#)</span></span>](walkthrough-using-only-stored-procedures-csharp.md)  
 <span data-ttu-id="7b6ee-127">Inclut des procédures qui expliquent comment utiliser des procédures stockées dans C#.</span><span class="sxs-lookup"><span data-stu-id="7b6ee-127">Includes procedures that illustrate how to use stored procedures in C#.</span></span>
