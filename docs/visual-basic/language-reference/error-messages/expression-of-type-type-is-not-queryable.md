---
title: L'expression de type '<type>' ne peut pas être interrogée
ms.date: 07/20/2015
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
ms.openlocfilehash: 78b47601bf0a013d079f638f6dac27511e01aec4
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874215"
---
# <a name="expression-of-type-type-is-not-queryable"></a><span data-ttu-id="b6efa-102">L'expression de type '\<type>' ne peut pas être interrogée</span><span class="sxs-lookup"><span data-stu-id="b6efa-102">Expression of type \<type> is not queryable</span></span>

<span data-ttu-id="b6efa-103">L’expression de type ne \<type> peut pas être interrogée.</span><span class="sxs-lookup"><span data-stu-id="b6efa-103">Expression of type \<type> is not queryable.</span></span> <span data-ttu-id="b6efa-104">Assurez-vous qu’il ne manque pas de référence d’assembly et/ou d’importation d’espace de noms pour le fournisseur LINQ.</span><span class="sxs-lookup"><span data-stu-id="b6efa-104">Make sure you are not missing an assembly reference and/or namespace import for the LINQ provider.</span></span>  
  
 <span data-ttu-id="b6efa-105">Les types interrogeables sont définis dans <xref:System.Linq> les <xref:System.Data.Linq> espaces de <xref:System.Xml.Linq> noms, et.</span><span class="sxs-lookup"><span data-stu-id="b6efa-105">Queryable types are defined in the <xref:System.Linq>, <xref:System.Data.Linq>, and <xref:System.Xml.Linq> namespaces.</span></span> <span data-ttu-id="b6efa-106">Vous devez importer un ou plusieurs de ces espaces de noms pour effectuer des requêtes LINQ.</span><span class="sxs-lookup"><span data-stu-id="b6efa-106">You must import one or more of these namespaces to perform LINQ queries.</span></span>  
  
 <span data-ttu-id="b6efa-107">L' <xref:System.Linq> espace de noms vous permet d’interroger des objets tels que des collections et des tableaux à l’aide de Linq.</span><span class="sxs-lookup"><span data-stu-id="b6efa-107">The <xref:System.Linq> namespace enables you to query objects such as collections and arrays by using LINQ.</span></span>  
  
 <span data-ttu-id="b6efa-108">L' <xref:System.Data.Linq> espace de noms vous permet d’interroger des jeux de données ADO.net et d’SQL Server des bases de données à l’aide de Linq.</span><span class="sxs-lookup"><span data-stu-id="b6efa-108">The <xref:System.Data.Linq> namespace enables you to query ADO.NET Datasets and SQL Server databases by using LINQ.</span></span>  
  
 <span data-ttu-id="b6efa-109">L' <xref:System.Xml.Linq> espace de noms vous permet d’interroger du code XML à l’aide de LINQ et d’utiliser des fonctionnalités XML dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b6efa-109">The <xref:System.Xml.Linq> namespace enables you to query XML by using LINQ and to use XML features in Visual Basic.</span></span>  
  
 <span data-ttu-id="b6efa-110">**ID d’erreur :** BC36593</span><span class="sxs-lookup"><span data-stu-id="b6efa-110">**Error ID:** BC36593</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b6efa-111">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="b6efa-111">To correct this error</span></span>  
  
1. <span data-ttu-id="b6efa-112">Ajoutez une `Import` instruction pour l' <xref:System.Linq> <xref:System.Data.Linq> espace de noms, ou <xref:System.Xml.Linq> à votre fichier de code.</span><span class="sxs-lookup"><span data-stu-id="b6efa-112">Add an `Import` statement for the <xref:System.Linq>, <xref:System.Data.Linq>, or <xref:System.Xml.Linq> namespace to your code file.</span></span> <span data-ttu-id="b6efa-113">Vous pouvez également importer des espaces de noms pour votre projet à l’aide de la page **références** du concepteur de projets (**My Project**).</span><span class="sxs-lookup"><span data-stu-id="b6efa-113">You can also import namespaces for your project by using the **References** page of the Project Designer (**My Project**).</span></span>  
  
2. <span data-ttu-id="b6efa-114">Assurez-vous que le type que vous avez identifié comme source de votre requête est un type pouvant être interrogé.</span><span class="sxs-lookup"><span data-stu-id="b6efa-114">Ensure that the type that you have identified as the source of your query is a queryable type.</span></span> <span data-ttu-id="b6efa-115">Autrement dit, un type qui implémente <xref:System.Collections.Generic.IEnumerable%601> ou <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="b6efa-115">That is, a type that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6efa-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6efa-116">See also</span></span>

- <xref:System.Linq>
- <xref:System.Data.Linq>
- <xref:System.Xml.Linq>
- [<span data-ttu-id="b6efa-117">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b6efa-117">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="b6efa-118">LINQ</span><span class="sxs-lookup"><span data-stu-id="b6efa-118">LINQ</span></span>](../../programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="b6efa-119">XML</span><span class="sxs-lookup"><span data-stu-id="b6efa-119">XML</span></span>](../../programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="b6efa-120">Références et instruction Imports</span><span class="sxs-lookup"><span data-stu-id="b6efa-120">References and the Imports Statement</span></span>](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="b6efa-121">Imports, instruction (espace de noms et type .NET)</span><span class="sxs-lookup"><span data-stu-id="b6efa-121">Imports Statement (.NET Namespace and Type)</span></span>](../statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="b6efa-122">Page Références, Concepteur de projets (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6efa-122">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
