---
title: 'Procédure pas à pas : Génération SQL'
ms.date: 03/30/2017
ms.assetid: 16c38aaa-9927-4f3c-ab0f-81636cce57a3
ms.openlocfilehash: 09b5a3c2dea5cd0483d617ee8064b41dc19c3374
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248293"
---
# <a name="walkthrough-sql-generation"></a><span data-ttu-id="d7db4-102">Procédure pas à pas : Génération SQL</span><span class="sxs-lookup"><span data-stu-id="d7db4-102">Walkthrough: SQL Generation</span></span>

<span data-ttu-id="d7db4-103">Cette rubrique montre comment la génération SQL se produit dans l' [exemple de fournisseur](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0).</span><span class="sxs-lookup"><span data-stu-id="d7db4-103">This topic illustrates how SQL generation occurs in the [Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0).</span></span> <span data-ttu-id="d7db4-104">La requête Entity SQL suivante utilise le modèle inclus dans le fournisseur d'exemples :</span><span class="sxs-lookup"><span data-stu-id="d7db4-104">The following Entity SQL query uses the model that is included with the sample provider:</span></span>

```sql
SELECT  j1.ProductId, j1.ProductName, j1.CategoryName, j2.ShipCountry, j2.ProductId
FROM (  SELECT P.ProductName, P.ProductId, P.Category.CategoryName
        FROM NorthwindEntities.Products AS P) as j1
INNER JOIN (SELECT OD.ProductId, OD.Order.ShipCountry as ShipCountry
            FROM NorthwindEntities.OrderDetails AS OD) as j2
            ON j1.ProductId == j2.ProductId
```

<span data-ttu-id="d7db4-105">La requête produit l'arborescence de commandes de sortie suivante passée au fournisseur :</span><span class="sxs-lookup"><span data-stu-id="d7db4-105">The query produces the following output command tree that is passed to the provider:</span></span>

```
DbQueryCommandTree
|_Parameters
|_Query : Collection{Record['C1'=Edm.Int32, 'ProductID'=Edm.Int32, 'ProductName'=Edm.String, 'CategoryName'=Edm.String, 'ShipCountry'=Edm.String, 'ProductID1'=Edm.Int32]}
  |_Project
    |_Input : 'Join4'
    | |_InnerJoin
    |   |_Left : 'Join1'
    |   | |_LeftOuterJoin
    |   |   |_Left : 'Extent1'
    |   |   | |_Scan : dbo.Products
    |   |   |_Right : 'Extent2'
    |   |   | |_Scan : dbo.Categories
    |   |   |_JoinCondition
    |   |     |_
    |   |       |_Var(Extent1).CategoryID
    |   |       |_=
    |   |       |_Var(Extent2).CategoryID
    |   |_Right : 'Join3'
    |   | |_LeftOuterJoin
    |   |   |_Left : 'Extent3'
    |   |   | |_Scan : dbo.OrderDetails
    |   |   |_Right : 'Join2'
    |   |   | |_LeftOuterJoin
    |   |   |   |_Left : 'Extent4'
    |   |   |   | |_Scan : dbo.Orders
    |   |   |   |_Right : 'Extent5'
    |   |   |   | |_Scan : dbo.InternationalOrders
    |   |   |   |_JoinCondition
    |   |   |     |_
    |   |   |       |_Var(Extent4).OrderID
    |   |   |       |_=
    |   |   |       |_Var(Extent5).OrderID
    |   |   |_JoinCondition
    |   |     |_
    |   |       |_Var(Extent3).OrderID
    |   |       |_=
    |   |       |_Var(Join2).Extent4.OrderID
    |   |_JoinCondition
    |     |_
    |       |_Var(Join1).Extent1.ProductID
    |       |_=
    |       |_Var(Join3).Extent3.ProductID
    |_Projection
      |_NewInstance : Record['C1'=Edm.Int32, 'ProductID'=Edm.Int32, 'ProductName'=Edm.String, 'CategoryName'=Edm.String, 'ShipCountry'=Edm.String, 'ProductID1'=Edm.Int32]
        |_Column : 'C1'
        | |_1
        |_Column : 'ProductID'
        | |_Var(Join4).Join1.Extent1.ProductID
        |_Column : 'ProductName'
        | |_Var(Join4).Join1.Extent1.ProductName
        |_Column : 'CategoryName'
        | |_Var(Join4).Join1.Extent2.CategoryName
        |_Column : 'ShipCountry'
        | |_Var(Join4).Join3.Join2.Extent4.ShipCountry
        |_Column : 'ProductID1'
          |_Var(Join4).Join3.Extent3.ProductID
```

 <span data-ttu-id="d7db4-106">Cette rubrique décrit la manière dont cette arborescence de commandes de sortie est traduite en instructions SQL suivantes.</span><span class="sxs-lookup"><span data-stu-id="d7db4-106">This topic describes how to translate this output command tree into the following SQL statements.</span></span>

```sql
SELECT
1 AS [C1],
[Extent1].[ProductID] AS [ProductID],
[Extent1].[ProductName] AS [ProductName],
[Extent2].[CategoryName] AS [CategoryName],
[Join3].[ShipCountry] AS [ShipCountry],
[Join3].[ProductID] AS [ProductID1]
FROM   [dbo].[Products] AS [Extent1]
LEFT OUTER JOIN [dbo].[Categories] AS [Extent2] ON [Extent1].[CategoryID] = [Extent2].[CategoryID]
INNER JOIN
(SELECT [Extent3].[OrderID] AS [OrderID1], [Extent3].[ProductID] AS [ProductID], [Extent3].[UnitPrice] AS [UnitPrice], [Extent3].[Quantity] AS [Quantity], [Extent3].[Discount] AS [Discount], [Join2].[OrderID2], [Join2].[CustomerID], [Join2].[EmployeeID], [Join2].[OrderDate], [Join2].[RequiredDate], [Join2].[ShippedDate], [Join2].[Freight], [Join2].[ShipName], [Join2].[ShipAddress], [Join2].[ShipCity], [Join2].[ShipRegion], [Join2].[ShipPostalCode], [Join2].[ShipCountry], [Join2].[OrderID3], [Join2].[CustomsDescription], [Join2].[ExciseTax]
FROM  [dbo].[OrderDetails] AS [Extent3]
LEFT OUTER JOIN
      (SELECT [Extent4].[OrderID] AS [OrderID2], [Extent4].[CustomerID] AS [CustomerID], [Extent4].[EmployeeID] AS [EmployeeID], [Extent4].[OrderDate] AS [OrderDate], [Extent4].[RequiredDate] AS [RequiredDate], [Extent4].[ShippedDate] AS [ShippedDate], [Extent4].[Freight] AS [Freight], [Extent4].[ShipName] AS [ShipName], [Extent4].[ShipAddress] AS [ShipAddress], [Extent4].[ShipCity] AS [ShipCity], [Extent4].[ShipRegion] AS [ShipRegion], [Extent4].[ShipPostalCode] AS [ShipPostalCode], [Extent4].[ShipCountry] AS [ShipCountry], [Extent5].[OrderID] AS [OrderID3], [Extent5].[CustomsDescription] AS [CustomsDescription], [Extent5].[ExciseTax] AS [ExciseTax]
FROM  [dbo].[Orders] AS [Extent4]
LEFT OUTER JOIN [dbo].[InternationalOrders] AS [Extent5] ON [Extent4].[OrderID] = [Extent5].[OrderID]
      ) AS [Join2] ON [Extent3].[OrderID] = [Join2].[OrderID2]
   ) AS [Join3] ON [Extent1].[ProductID] = [Join3].[ProductID]
```

## <a name="first-phase-of-sql-generation-visiting-the-expression-tree"></a><span data-ttu-id="d7db4-107">Première phase de la génération SQL : Visite de l’arborescence de l’expression</span><span class="sxs-lookup"><span data-stu-id="d7db4-107">First Phase of SQL Generation: Visiting the Expression Tree</span></span>

<span data-ttu-id="d7db4-108">La figure suivante illustre l'état vide initial du visiteur.</span><span class="sxs-lookup"><span data-stu-id="d7db4-108">The following figure illustrates the initial empty state of the visitor.</span></span>  <span data-ttu-id="d7db4-109">Dans l'ensemble de cette rubrique, seules les propriétés pertinentes pour l'explication de la procédure pas à pas sont présentées.</span><span class="sxs-lookup"><span data-stu-id="d7db4-109">Throughout this topic, only the properties relevant to the walkthrough explanation are shown.</span></span>

<span data-ttu-id="d7db4-110">![Diagramme](./media/430180f5-4fb9-4bc3-8589-d566512d9703.gif "430180f5-4fb9-4bc3-8589-d566512d9703")</span><span class="sxs-lookup"><span data-stu-id="d7db4-110">![Diagram](./media/430180f5-4fb9-4bc3-8589-d566512d9703.gif "430180f5-4fb9-4bc3-8589-d566512d9703")</span></span>

<span data-ttu-id="d7db4-111">Lorsque le nœud Projet est visité, VisitInputExpression est appelé sur son entrée (Join4), qui déclenche la visite de Join4 par la méthode VisitJoinExpression.</span><span class="sxs-lookup"><span data-stu-id="d7db4-111">When the Project  node is visited, VisitInputExpression is called over its input (Join4), which triggers the visit of Join4 by the method VisitJoinExpression.</span></span> <span data-ttu-id="d7db4-112">En sa qualité de jointure supérieure, IsParentAJoin retourne la valeur false et un nouveau SqlSelectStatement (SelectStatement0) est créé et ajouté à la pile d'instructions SELECT.</span><span class="sxs-lookup"><span data-stu-id="d7db4-112">Because this is a topmost join, IsParentAJoin returns false and a new SqlSelectStatement (SelectStatement0) is created and pushed on the SELECT statement stack.</span></span> <span data-ttu-id="d7db4-113">De même, une nouvelle étendue (scope0) est entrée dans la table de symboles.</span><span class="sxs-lookup"><span data-stu-id="d7db4-113">Also, a new scope (scope0) is entered in the symbol table.</span></span> <span data-ttu-id="d7db4-114">Avant que la première entrée (gauche) de la jointure soit visitée, la valeur 'true' est ajoutée à la pile IsParentAJoin.</span><span class="sxs-lookup"><span data-stu-id="d7db4-114">Before the first (left) input of the join is visited, 'true' is pushed on the IsParentAJoin stack.</span></span> <span data-ttu-id="d7db4-115">Juste avant que Join1, qui est l'entrée gauche de Join4, soit visitée, l'état du visiteur est celui illustré dans la figure suivante.</span><span class="sxs-lookup"><span data-stu-id="d7db4-115">Right before Join1, which is the left input of Join4, is visited, the state of the visitor is as shown in the next figure.</span></span>

<span data-ttu-id="d7db4-116">![Diagramme](./media/406d4f5f-6166-44ea-8e74-c5001d5d5d79.gif "406d4f5f-6166-44ea-8e74-c5001d5d5d79")</span><span class="sxs-lookup"><span data-stu-id="d7db4-116">![Diagram](./media/406d4f5f-6166-44ea-8e74-c5001d5d5d79.gif "406d4f5f-6166-44ea-8e74-c5001d5d5d79")</span></span>

<span data-ttu-id="d7db4-117">Lorsque la méthode de visite de jointure est appelée sur Join4, IsParentAJoin a la valeur true et réutilise donc l'instruction SELECT SelectStatement0 actuelle.</span><span class="sxs-lookup"><span data-stu-id="d7db4-117">When the join visit method is invoked over Join4, IsParentAJoin is true, thus it reuses the current select statement SelectStatement0.</span></span> <span data-ttu-id="d7db4-118">Une nouvelle étendue est entrée (scope1).</span><span class="sxs-lookup"><span data-stu-id="d7db4-118">A new scope is entered (scope1).</span></span> <span data-ttu-id="d7db4-119">Avant de visiter son enfant gauche, Extent1, une autre valeur true est ajoutée à la pile IsParentAJoin.</span><span class="sxs-lookup"><span data-stu-id="d7db4-119">Before visiting its left child, Extent1, another true is pushed on the IsParentAJoin stack.</span></span>

<span data-ttu-id="d7db4-120">Lorsque IsParentAJoin retourne la valeur true et que Extent1 est visité, un SqlBuilder contenant « [dbo].[Products] » est retourné.</span><span class="sxs-lookup"><span data-stu-id="d7db4-120">When Extent1 is visited, because IsParentAJoin returns true, it returns a SqlBuilder containing "[dbo].[Products]".</span></span> <span data-ttu-id="d7db4-121">Le contrôle retourne à la méthode qui visite Join4.</span><span class="sxs-lookup"><span data-stu-id="d7db4-121">The control returns to the method visiting Join4.</span></span> <span data-ttu-id="d7db4-122">Une entrée est dépilée de IsParentAJoin et ProcessJoinInputResult est appelé, ce qui ajoute le résultat de la visite de Extent1 à la clause From de SelectStatement0.</span><span class="sxs-lookup"><span data-stu-id="d7db4-122">An entry is popped from IsParentAJoin, and ProcessJoinInputResult is called, which appends the result of visiting Extent1 to the From clause of SelectStatement0.</span></span> <span data-ttu-id="d7db4-123">Un nouveau symbole FROM, symbol_Extent1, est créé pour le nom de liaison d'entrée « Extent1 » et ajouté aux FromExtents de SelectStatement0, de même que « As » et symbol_Extent1 sont ajoutés à la clause FROM.</span><span class="sxs-lookup"><span data-stu-id="d7db4-123">A new from symbol, symbol_Extent1, for the input binding name "Extent1" is created, added to the FromExtents of SelectStatement0, and also "As" and  symbol_Extent1 are appended to the from clause.</span></span> <span data-ttu-id="d7db4-124">Une nouvelle entrée est ajoutée à AllExtentNames pour « Extent1 » avec la valeur 0.</span><span class="sxs-lookup"><span data-stu-id="d7db4-124">A new entry is added to AllExtentNames for "Extent1" with the value of 0.</span></span> <span data-ttu-id="d7db4-125">Une nouvelle entrée est ajoutée à l'étendue actuelle dans la table de symboles pour associer « Extent1 » à son symbole symbol_Extent1.</span><span class="sxs-lookup"><span data-stu-id="d7db4-125">A new entry is added to the current scope in the symbol table to associate "Extent1" with its symbol symbol_Extent1.</span></span> <span data-ttu-id="d7db4-126">Symbol_Extent1 est également ajouté aux AllJoinExtents de SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="d7db4-126">Symbol_Extent1 is also added to the AllJoinExtents of the SqlSelectStatement.</span></span>

<span data-ttu-id="d7db4-127">Avant que l'entrée droite de Join1 soit visitée, « LEFT OUTER JOIN » est ajouté à la clause FROM de SelectStatement0.</span><span class="sxs-lookup"><span data-stu-id="d7db4-127">Before the right input of Join1 is visited, "LEFT OUTER JOIN" is added to the From clause of SelectStatement0.</span></span> <span data-ttu-id="d7db4-128">L'entrée droite étant une expression SCAN, la valeur true est à nouveau ajoutée à la pile IsParentAJoin.</span><span class="sxs-lookup"><span data-stu-id="d7db4-128">Because the right input is a Scan expression, true is again pushed to the IsParentAJoin stack.</span></span> <span data-ttu-id="d7db4-129">L'état avant la visite de l'entrée droite est illustré dans la figure suivante.</span><span class="sxs-lookup"><span data-stu-id="d7db4-129">The state before visiting the right input as shown in the next figure.</span></span>

<span data-ttu-id="d7db4-130">![Diagramme](./media/ca62c31b-7ff6-4836-b209-e16166304fdc.gif "ca62c31b-7ff6-4836-B209-e16166304fdc")</span><span class="sxs-lookup"><span data-stu-id="d7db4-130">![Diagram](./media/ca62c31b-7ff6-4836-b209-e16166304fdc.gif "ca62c31b-7ff6-4836-b209-e16166304fdc")</span></span>

<span data-ttu-id="d7db4-131">L'entrée droite est traitée de la même façon que l'entrée gauche.</span><span class="sxs-lookup"><span data-stu-id="d7db4-131">The right input is processed in the same way as the left input.</span></span> <span data-ttu-id="d7db4-132">L'état après la visite de l'entrée droite est illustré dans la figure suivante.</span><span class="sxs-lookup"><span data-stu-id="d7db4-132">The state after visiting the right input is shown in the next figure.</span></span>

<span data-ttu-id="d7db4-133">![Diagram](./media/cd2afa99-7256-4c63-aaa9-c2d13f18a3d8.gif "cd2afa99-7256-4c63-aaa9-c2d13f18a3d8")</span><span class="sxs-lookup"><span data-stu-id="d7db4-133">![Diagram](./media/cd2afa99-7256-4c63-aaa9-c2d13f18a3d8.gif "cd2afa99-7256-4c63-aaa9-c2d13f18a3d8")</span></span>

<span data-ttu-id="d7db4-134">La valeur « false » suivante est ajoutée à la pile IsParentAJoin et la condition de jointure Var(Extent1).CategoryID == Var(Extent2).CategoryID est traitée.</span><span class="sxs-lookup"><span data-stu-id="d7db4-134">Next "false" is pushed on the IsParentAJoin stack and the join condition Var(Extent1).CategoryID == Var(Extent2).CategoryID is processed.</span></span> <span data-ttu-id="d7db4-135">Var (Extent1) est résolu en \<symbol_Extent1 > après une recherche dans la table de symboles.</span><span class="sxs-lookup"><span data-stu-id="d7db4-135">Var(Extent1) is resolved to \<symbol_Extent1> after a look up in the symbol table.</span></span> <span data-ttu-id="d7db4-136">Étant donné que l’instance est résolue en un symbole simple, à la suite du traitement de var (Extent1). CategoryID, SqlBuilder avec \<Symbol1 >». CategoryID» est retourné.</span><span class="sxs-lookup"><span data-stu-id="d7db4-136">Because the instance is resolved to a simple Symbol, as a result of processing Var(Extent1).CategoryID, a SqlBuilder with \<symbol1>."CategoryID" is returned.</span></span> <span data-ttu-id="d7db4-137">De la même façon, l'autre partie de la comparaison est traitée et le résultat de la visite de la condition de jointure est ajouté à la clause FROM de SelectStatement1 et la valeur « false » est retirée de la pile IsParentAJoin.</span><span class="sxs-lookup"><span data-stu-id="d7db4-137">Similarly the other side of the comparison is processed, and the result of visiting the join condition is appended to the FROM clause of SelectStatement1 and the value "false" is popped from the IsParentAJoin stack.</span></span>

<span data-ttu-id="d7db4-138">Avec ceci, Join1 a été traité complètement et une étendue est dépilée de la table de symboles.</span><span class="sxs-lookup"><span data-stu-id="d7db4-138">With this, Join1 has completely been processed, and a scope is popped from the symbol table.</span></span>

<span data-ttu-id="d7db4-139">Le contrôle retourne au traitement de Join4, le parent de Join1.</span><span class="sxs-lookup"><span data-stu-id="d7db4-139">Control returns to processing Join4, the parent of Join1.</span></span> <span data-ttu-id="d7db4-140">Étant donné que l’enfant réutilise l’instruction SELECT, les étendues Join1 sont remplacées par un \<symbole de jointure unique joinSymbol_Join1 >.</span><span class="sxs-lookup"><span data-stu-id="d7db4-140">Because the child reused the Select statement, the Join1 extents are replaced with a single Join symbol \<joinSymbol_Join1>.</span></span> <span data-ttu-id="d7db4-141">Une nouvelle entrée est également ajoutée à la table de symboles pour associer Join1 \<à joinSymbol_Join1 >.</span><span class="sxs-lookup"><span data-stu-id="d7db4-141">Also a new entry is added to the symbol table to associate Join1 with \<joinSymbol_Join1>.</span></span>

<span data-ttu-id="d7db4-142">Le nœud suivant à traiter est Join3, le deuxième enfant de Join4.</span><span class="sxs-lookup"><span data-stu-id="d7db4-142">The next node to be processed is Join3, the second child of Join4.</span></span> <span data-ttu-id="d7db4-143">En tant qu'enfant droit, la valeur « false » est ajoutée à la pile IsParentAJoin.</span><span class="sxs-lookup"><span data-stu-id="d7db4-143">As it is a right child, "false" is pushed to the IsParentAJoin stack.</span></span> <span data-ttu-id="d7db4-144">L'état du visiteur à ce stade est illustré dans la figure suivante.</span><span class="sxs-lookup"><span data-stu-id="d7db4-144">The state of the visitor at this point is illustrated in the next figure.</span></span>

<span data-ttu-id="d7db4-145">![Diagramme](./media/1ec61ed3-fcdd-4649-9089-24385be7e423.gif "1ec61ed3-FCDD-4649-9089-24385be7e423")</span><span class="sxs-lookup"><span data-stu-id="d7db4-145">![Diagram](./media/1ec61ed3-fcdd-4649-9089-24385be7e423.gif "1ec61ed3-fcdd-4649-9089-24385be7e423")</span></span>

<span data-ttu-id="d7db4-146">Pour Join3, IsParentAJoin retourne la valeur false et doit démarrer un nouveau SqlSelectStatement (SelectStatement1) et l'ajouter à la pile.</span><span class="sxs-lookup"><span data-stu-id="d7db4-146">For Join3, IsParentAJoin returns false and needs to start a new SqlSelectStatement (SelectStatement1) and push it on the stack.</span></span> <span data-ttu-id="d7db4-147">Le traitement continue comme pour les jointures précédentes, une nouvelle étendue est ajoutée à la pile et les enfants sont traités.</span><span class="sxs-lookup"><span data-stu-id="d7db4-147">Processing continues as it did with the previous the previous joins, a new scope is pushed on the stack and the children are processed.</span></span> <span data-ttu-id="d7db4-148">L’enfant de gauche est une étendue (Extent3) et le bon enfant est une jointure (Join2) qui doit également démarrer un nouveau SqlSelectStatement : SelectStatement2.</span><span class="sxs-lookup"><span data-stu-id="d7db4-148">The left child is an Extent (Extent3) and the right child is a join (Join2) which also needs to start a new SqlSelectStatement: SelectStatement2.</span></span> <span data-ttu-id="d7db4-149">Les enfants sur Join2 sont également des étendues et sont regroupés dans SelectStatement2.</span><span class="sxs-lookup"><span data-stu-id="d7db4-149">The children on Join2 are Extents as well and are aggregated into SelectStatement2.</span></span>

<span data-ttu-id="d7db4-150">L'état du visiteur une fois Join2 visité, mais avant que son post-traitement (ProcessJoinInputResult) soit effectué, est illustré dans la figure suivante :</span><span class="sxs-lookup"><span data-stu-id="d7db4-150">The state of the visitor right after Join2 is visited, but before its post-processing (ProcessJoinInputResult) is done is shown in the next figure:</span></span>

<span data-ttu-id="d7db4-151">![Diagramme](./media/7510346f-8b09-4c99-b411-40af239c3c4d.gif "7510346f-8b09-4C99-B411-40af239c3c4d")</span><span class="sxs-lookup"><span data-stu-id="d7db4-151">![Diagram](./media/7510346f-8b09-4c99-b411-40af239c3c4d.gif "7510346f-8b09-4c99-b411-40af239c3c4d")</span></span>

<span data-ttu-id="d7db4-152">Dans la figure précédente, SelectStatement2 est flottant parce qu'il a été retiré de la pile, mais pas encore post-traité par le parent.</span><span class="sxs-lookup"><span data-stu-id="d7db4-152">In the previous figure, SelectStatement2 is shown as free floating because it was popped out of the stack, but not yet post processed by the parent.</span></span> <span data-ttu-id="d7db4-153">Il doit être ajouté à la partie FROM du parent, mais sans cause SELECT, ce n'est pas une instruction SQL complète.</span><span class="sxs-lookup"><span data-stu-id="d7db4-153">It needs to be added to the FROM part of the parent, but it is not a complete SQL statement without a SELECT clause.</span></span> <span data-ttu-id="d7db4-154">Ainsi, à ce stade, les colonnes par défaut (toutes les colonnes produites par ses entrées) sont ajoutées à la liste de sélection par la méthode AddDefaultColumns.</span><span class="sxs-lookup"><span data-stu-id="d7db4-154">So, at this point, the default columns (all the columns produced by its inputs) are added to the select list by the method AddDefaultColumns.</span></span> <span data-ttu-id="d7db4-155">AddDefaultColumns effectue une itération sur les symboles dans FromExtents et pour chaque symbole ajoute toutes les colonnes de l'étendue.</span><span class="sxs-lookup"><span data-stu-id="d7db4-155">AddDefaultColumns iterates over the symbols in FromExtents and for each symbol adds all the columns brought in scope.</span></span> <span data-ttu-id="d7db4-156">Pour un symbole simple, il regarde le type de symbole afin de récupérer toutes ses propriétés à ajouter.</span><span class="sxs-lookup"><span data-stu-id="d7db4-156">For a simple symbol, it looks at the symbol type to retrieve all its properties to be added.</span></span> <span data-ttu-id="d7db4-157">Il remplit également le dictionnaire AllColumnNames avec les noms des colonnes.</span><span class="sxs-lookup"><span data-stu-id="d7db4-157">It also populates the AllColumnNames dictionary with the column names.</span></span> <span data-ttu-id="d7db4-158">Le SelectStatement2 complété est ajouté à la clause FROM de SelectStatement1.</span><span class="sxs-lookup"><span data-stu-id="d7db4-158">The completed SelectStatement2 is appended to the FROM clause of SelectStatement1.</span></span>

<span data-ttu-id="d7db4-159">Un symbole de jointure est ensuite créé pour représenter Join2, il est marqué comme une jointure imbriquée et ajouté aux AllJoinExtents de SelectStatement1 et à la table de symboles.</span><span class="sxs-lookup"><span data-stu-id="d7db4-159">Next, a new join symbol is created to represent Join2, it is marked as a nested join and added to the AllJoinExtents of SelectStatement1 and added to the symbol table.</span></span>  <span data-ttu-id="d7db4-160">Maintenant la condition de jointure de Join3, Var(Extent3).OrderID = Var(Join2).Extent4.OrderID, doit être traitée.</span><span class="sxs-lookup"><span data-stu-id="d7db4-160">Now the join condition of Join3, Var(Extent3).OrderID =  Var(Join2).Extent4.OrderID, needs to be processed.</span></span> <span data-ttu-id="d7db4-161">Le traitement de la partie gauche est semblable à la condition de jointure de Join1.</span><span class="sxs-lookup"><span data-stu-id="d7db4-161">Processing of the left hand side is similar to the join condition of Join1.</span></span> <span data-ttu-id="d7db4-162">Toutefois, le traitement de la partie droite « Var(Join2).Extent4.OrderID » est différent parce que l'aplanissement de jointure est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="d7db4-162">However, the processing of the right and side "Var(Join2).Extent4.OrderID" is different because join flattening is required.</span></span>

<span data-ttu-id="d7db4-163">La figure suivante illustre l'état du visiteur juste avant que le DbPropertyExpression « Var(Join2).Extent4.OrderID » soit traité.</span><span class="sxs-lookup"><span data-stu-id="d7db4-163">The next figure shows the state of the visitor right before the DbPropertyExpression "Var(Join2).Extent4.OrderID" is processed.</span></span>

<span data-ttu-id="d7db4-164">Considérez la façon dont « Var(Join2).Extent4.OrderID » est visité.</span><span class="sxs-lookup"><span data-stu-id="d7db4-164">Consider how "Var(Join2).Extent4.OrderID" is visited.</span></span> <span data-ttu-id="d7db4-165">Tout d'abord, la propriété d'instance « Var(Join2).Extent4 » qui est un autre DbPropertyExpression est visitée, et visite pour la première fois son instance « Var(Join2) ».</span><span class="sxs-lookup"><span data-stu-id="d7db4-165">First, the instance property "Var(Join2).Extent4" is visited, which is another DbPropertyExpression and first visits its instance "Var(Join2)".</span></span> <span data-ttu-id="d7db4-166">Dans l’étendue la plus haute de la table de symboles, « Join2 » est résolu \<en joinSymbol_join2 >.</span><span class="sxs-lookup"><span data-stu-id="d7db4-166">In the top most scope in the symbol table, "Join2" resolves to \<joinSymbol_join2>.</span></span> <span data-ttu-id="d7db4-167">Dans la méthode de visite utilisée par DbPropertyExpression pour traiter « Var(Join2).Extent4 », notez qu'un symbole de jointure a été retourné lors de la visite de l'instance et que l'aplanissement est obligatoire.</span><span class="sxs-lookup"><span data-stu-id="d7db4-167">In the visit method for DbPropertyExpression processing "Var(Join2).Extent4" notice that a join symbol was returned when visiting the instance and flattening is required.</span></span>

<span data-ttu-id="d7db4-168">Étant donné qu’il s’agit d’une jointure imbriquée, nous recherchons la propriété « Extent4 » dans le dictionnaire NameToExtent du symbole de \<jointure, nous la résolvons en symbol_Extent4\<> et retournons un nouveau SymbolPair (joinSymbol_join2 >, \<symbol_Extent4 >).</span><span class="sxs-lookup"><span data-stu-id="d7db4-168">Since it is a nested join, we look up the property "Extent4" in the NameToExtent dictionary of the join symbol, resolve it to \<symbol_Extent4> and return a new SymbolPair(\<joinSymbol_join2>, \<symbol_Extent4>).</span></span> <span data-ttu-id="d7db4-169">Dans la mesure où une paire de symboles est retournée à partir du traitement de l’instance de «var (Join2). Extent4. OrderID», la propriété « OrderID » est résolue à partir du ColumnPart de cette paire\<de symboles (symbol_Extent4 >), qui contient une liste des colonnes de l’étendue qu’il représente.</span><span class="sxs-lookup"><span data-stu-id="d7db4-169">Since a symbol pair is returned from the processing of the instance of "Var(Join2).Extent4.OrderID",  the property "OrderID" is resolved from the ColumnPart of that symbol pair (\<symbol_Extent4>), which has a list of the columns of the extent it represents.</span></span> <span data-ttu-id="d7db4-170">Ainsi, «var (Join2). Extent4. OrderID» est résolu en { \<joinSymbol_Join2 >, ".", \<symbol_OrderID >}.</span><span class="sxs-lookup"><span data-stu-id="d7db4-170">So, "Var(Join2).Extent4.OrderID" is resolved to { \<joinSymbol_Join2>, ".", \<symbol_OrderID>}.</span></span>

<span data-ttu-id="d7db4-171">La condition de jointure de Join4 est traitée de la même façon.</span><span class="sxs-lookup"><span data-stu-id="d7db4-171">The join condition of Join4 is similarly processed.</span></span> <span data-ttu-id="d7db4-172">Le contrôle retourne à la méthode VisitInputExpression qui a traité le projet supérieur.</span><span class="sxs-lookup"><span data-stu-id="d7db4-172">The control returns to the VisitInputExpression method that processed the top most project.</span></span> <span data-ttu-id="d7db4-173">En observant les FromExtents du SelectStatement0 retourné, l'entrée est identifiée en tant que jointure et supprime les étendues d'origine en les remplaçant par une nouvelle étendue avec seulement le symbole de jointure.</span><span class="sxs-lookup"><span data-stu-id="d7db4-173">Looking at the FromExtents of the returned SelectStatement0, the input is identified as a join, and removes the original extents and replaces them with a new extent with just the Join symbol.</span></span> <span data-ttu-id="d7db4-174">La table de symboles est également mise à jour puis la partie de projection du projet est traitée.</span><span class="sxs-lookup"><span data-stu-id="d7db4-174">The symbol table is also updated and next the projection part of the Project is processed.</span></span> <span data-ttu-id="d7db4-175">La résolution des propriétés et l'aplanissement des étendues de jointure s'effectuent comme décrit précédemment.</span><span class="sxs-lookup"><span data-stu-id="d7db4-175">The resolving of the properties and the flattening of the join extents is as described earlier.</span></span>

<span data-ttu-id="d7db4-176">![Diagramme](./media/9456d6a9-ea2e-40ae-accc-a10e18e28b81.gif "9456d6a9-ea2e-40AE-ACCC-a10e18e28b81")</span><span class="sxs-lookup"><span data-stu-id="d7db4-176">![Diagram](./media/9456d6a9-ea2e-40ae-accc-a10e18e28b81.gif "9456d6a9-ea2e-40ae-accc-a10e18e28b81")</span></span>

<span data-ttu-id="d7db4-177">Enfin, le SqlSelectStatement suivant est produit :</span><span class="sxs-lookup"><span data-stu-id="d7db4-177">Finally, the following SqlSelectStatement is produced:</span></span>

```
SELECT:
  "1", " AS ", "[C1]",
  <symbol_Extent1>, ".", "[ProductID]", " AS ", "[ProductID]",
  <symbol_Extent1>, ".", "[ProductName]", " AS ", "[ProductName]",
  <symbol_Extent2>, ".", "[CategoryName]", " AS ", "[CategoryName]",
  <joinSymbol_Join3>, ".", <symbol_ShipCountry>, " AS ", "[ShipCountry]",
  <joinSymbol_Join3>, ".", <symbol_ProductID>, " AS ", "[ProductID1]"
FROM: "[dbo].[Products]", " AS ", <symbol_Extent1>,
        "LEFT OUTER JOIN ""[dbo].[Categories]", " AS ", <symbol_Extent2>, " ON ", <symbol_Extent1>, ".", "[CategoryID]", " = ", <symbol_Extent2>, ".", "[CategoryID]",
        "INNER JOIN ",
        " (", SELECT:
           <symbol_Extent3>, ".", "[OrderID]", " AS ", <symbol_OrderID>, ",
              <symbol_Extent3>, ".", "[ProductID]", " AS ", <symbol_ProductID>, ...,
         <joinSymbol_Join2>, ".", <symbol_OrderID_2>, ", ",
           <joinSymbol_Join2>, ".", <symbol_CustomerID>, ....,
        <joinSymbol_Join2>, ".", <symbol_OrderID_3>,
<joinSymbol_Join2>, ".", <symbol_CustomsDescription>,
<joinSymbol_Join2>, ".", <symbol_ExciseTax>
FROM: "[dbo].[OrderDetails]", " AS ", <symbol_Extent3>,
"LEFT OUTER JOIN ",
" (", SELECT:
<symbol_Extent4>, ".", "[OrderID]", " AS ", <symbol_OrderID_2>,
<symbol_Extent4>, ".", "[CustomerID]", " AS ", <symbol_CustomerID>, ...
<symbol_Extent5>, ".", "[OrderID]", " AS ", <symbol_OrderID_3>,
<symbol_Extent5>, ".", "[CustomsDescription]", " AS ", <symbol_CustomsDescription>,
<symbol_Extent5>, ".", "[ExciseTax]", " AS ", <symbol_ExciseTax>
FROM: "[dbo].[Orders]", " AS ", <symbol_Extent4>,
"LEFT OUTER JOIN ", , "[dbo].[InternationalOrders]", " AS ", <symbol_Extent5>,
" ON ", <symbol_Extent4>, ".", "[OrderID]", " = ", , <symbol_Extent5>, ".", "[OrderID]"
" )", " AS ", <joinSymbol_Join2>, " ON ", , , <symbol_Extent3>, ".", "[OrderID]", " = ", , <joinSymbol_Join2>, ".", <symbol_OrderID_2>
" )", " AS ", <joinSymbol_Join3>, " ON ", , , <symbol_Extent1>, ".", "[ProductID]", " = ", , <joinSymbol_Join3>, ".", <symbol_ProductID>
```

### <a name="second-phase-of-sql-generation-generating-the-string-command"></a><span data-ttu-id="d7db4-178">Deuxième phase de la génération SQL : Génération de la commande de chaîne</span><span class="sxs-lookup"><span data-stu-id="d7db4-178">Second Phase of SQL Generation: Generating the String Command</span></span>

<span data-ttu-id="d7db4-179">La deuxième phase produit des noms réels pour les symboles et seuls sont considérés les symboles qui représentent des colonnes nommées « OrderID », puisque dans ce cas un conflit doit être résolu.</span><span class="sxs-lookup"><span data-stu-id="d7db4-179">The second phase produces actual names for the symbols, and we only focus on the symbols representing columns named "OrderID", as in this case a conflict needs to be resolved.</span></span> <span data-ttu-id="d7db4-180">Ceux-ci sont mis en surbrillance dans le SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="d7db4-180">These are highlighted in the SqlSelectStatement.</span></span> <span data-ttu-id="d7db4-181">Notez que les suffixes utilisés dans la figure permettent uniquement d'insister sur le fait que ce sont des instances différentes et non de représenter de nouveaux noms, puisque, à ce stade, leurs noms définitifs (pouvant être différents des noms d'origine) n'ont pas encore été assignés.</span><span class="sxs-lookup"><span data-stu-id="d7db4-181">Note that the suffixes used in the figure are only to emphasize that these are different instances, not to represent any new names, as at this stage their final names (possibly different form the original names) have not been assigned yet.</span></span>

<span data-ttu-id="d7db4-182">Le premier symbole trouvé qui doit être renommé est \<symbol_OrderID >.</span><span class="sxs-lookup"><span data-stu-id="d7db4-182">The first symbol found that needs to be renamed is \<symbol_OrderID>.</span></span> <span data-ttu-id="d7db4-183">Son nouveau nom est « OrderID1 », 1 est marqué en tant que dernier suffixe utilisé pour « OrderID » et le symbole est marqué comme ne devant pas être renommé.</span><span class="sxs-lookup"><span data-stu-id="d7db4-183">Its new name is assigned as "OrderID1", 1 is marked as the last used suffix for "OrderID" and the symbol is marked as not needing renaming.</span></span> <span data-ttu-id="d7db4-184">Ensuite, la première utilisation de \<symbol_OrderID_2 > est trouvée.</span><span class="sxs-lookup"><span data-stu-id="d7db4-184">Next, the first usage of \<symbol_OrderID_2> is found.</span></span> <span data-ttu-id="d7db4-185">Il est renommé pour utiliser le suffixe disponible suivant (« OrderID2 ») et est encore marqué comme ne devant pas être renommé afin qu'à sa prochaine utilisation il ne soit pas renommé.</span><span class="sxs-lookup"><span data-stu-id="d7db4-185">It is renamed to use the next available suffix ("OrderID2") and again marked as not needing renaming, so that next time it is used it does not get renamed.</span></span> <span data-ttu-id="d7db4-186">Cela est également nécessaire \<pour symbol_OrderID_3 >.</span><span class="sxs-lookup"><span data-stu-id="d7db4-186">This is done for \<symbol_OrderID_3> too.</span></span>

<span data-ttu-id="d7db4-187">À la fin de la deuxième phase, la dernière instruction SQL est générée.</span><span class="sxs-lookup"><span data-stu-id="d7db4-187">At the end of the second phase, the final SQL statement is generated.</span></span>

## <a name="see-also"></a><span data-ttu-id="d7db4-188">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7db4-188">See also</span></span>

- [<span data-ttu-id="d7db4-189">Génération SQL dans l’exemple de fournisseur</span><span class="sxs-lookup"><span data-stu-id="d7db4-189">SQL Generation in the Sample Provider</span></span>](sql-generation-in-the-sample-provider.md)
