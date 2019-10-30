---
title: Architecture et conception
ms.date: 03/30/2017
ms.assetid: bd738d39-00e2-4bab-b387-90aac1a014bd
ms.openlocfilehash: 35fbc39db23a2b08ab926e122d2f1eb1806a369b
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040025"
---
# <a name="architecture-and-design"></a><span data-ttu-id="93650-102">Architecture et conception</span><span class="sxs-lookup"><span data-stu-id="93650-102">Architecture and Design</span></span>

<span data-ttu-id="93650-103">Le module de génération SQL de l' [exemple de fournisseur](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) est implémenté en tant que visiteur de l’arborescence d’expressions qui représente l’arborescence de commandes.</span><span class="sxs-lookup"><span data-stu-id="93650-103">The SQL generation module in the [Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) is implemented as a visitor on the expression tree that represents the command tree.</span></span> <span data-ttu-id="93650-104">La génération est effectuée par un unique passage sur l'arborescence de l'expression.</span><span class="sxs-lookup"><span data-stu-id="93650-104">The generation is done in a single pass over the expression tree.</span></span>

<span data-ttu-id="93650-105">Les nœuds de l’arborescence sont traités de bas en haut.</span><span class="sxs-lookup"><span data-stu-id="93650-105">The nodes of the tree are processed from the bottom up.</span></span> <span data-ttu-id="93650-106">En premier lieu, une structure intermédiaire est produite : SqlSelectStatement ou SqlBuilder, tous deux implémentant ISqlFragment.</span><span class="sxs-lookup"><span data-stu-id="93650-106">First, an intermediate structure is produced: SqlSelectStatement or SqlBuilder, both implementing ISqlFragment.</span></span> <span data-ttu-id="93650-107">Ensuite, l'instruction SQL de chaîne est issue de cette structure.</span><span class="sxs-lookup"><span data-stu-id="93650-107">Next, the string SQL statement is produced from that structure.</span></span> <span data-ttu-id="93650-108">Il y a deux raisons pour la structure intermédiaire :</span><span class="sxs-lookup"><span data-stu-id="93650-108">There are two reasons for the intermediate structure:</span></span>

- <span data-ttu-id="93650-109">Logiquement, une instruction SQL SELECT est remplie de manière désordonnée.</span><span class="sxs-lookup"><span data-stu-id="93650-109">Logically, a SQL SELECT statement is populated out of order.</span></span> <span data-ttu-id="93650-110">Les nœuds qui participent à la clause FROM sont visités avant les nœuds qui participent aux clauses WHERE, GROUP BY et ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="93650-110">The nodes that participate in the FROM clause are visited before the nodes that participate in the WHERE, GROUP BY, and the ORDER BY clause.</span></span>

- <span data-ttu-id="93650-111">Pour renommer des alias, vous devez identifier tous les alias utilisés afin d'éviter des conflits pendant le changement de nom.</span><span class="sxs-lookup"><span data-stu-id="93650-111">To rename aliases, you must identify all used aliases to avoid collisions during renaming.</span></span> <span data-ttu-id="93650-112">Pour différer les choix de changement de nom dans SqlBuilder, utilisez des objets Symbol afin de représenter les colonnes candidates pour le changement de nom.</span><span class="sxs-lookup"><span data-stu-id="93650-112">To defer the renaming choices in SqlBuilder, use Symbol objects to represent the columns that are candidates for renaming.</span></span>

<span data-ttu-id="93650-113">![Diagramme](./media/de1ca705-4f7c-4d2d-ace5-afefc6d3cefa.gif "de1ca705-4f7c-4d2d-ace5-afefc6d3cefa")</span><span class="sxs-lookup"><span data-stu-id="93650-113">![Diagram](./media/de1ca705-4f7c-4d2d-ace5-afefc6d3cefa.gif "de1ca705-4f7c-4d2d-ace5-afefc6d3cefa")</span></span>

<span data-ttu-id="93650-114">Dans la première phase, lors de la visite de l’arborescence de l’expression, les expressions sont groupées dans SqlSelectStatements, les jointures sont aplanies de même que les alias de jointure.</span><span class="sxs-lookup"><span data-stu-id="93650-114">In the first phase, while visiting the expression tree, expressions are grouped into SqlSelectStatements, joins are flattened, and join aliases are flattened.</span></span> <span data-ttu-id="93650-115">Pendant ce passage, les objets Symbol représentent des colonnes ou des alias d'entrée qui peuvent être renommés.</span><span class="sxs-lookup"><span data-stu-id="93650-115">During this pass, Symbol objects represent columns or input aliases that may be renamed.</span></span>

<span data-ttu-id="93650-116">Dans la deuxième phase, lors de la production de la chaîne réelle, les alias sont renommés.</span><span class="sxs-lookup"><span data-stu-id="93650-116">In the second phase, while producing the actual string, aliases are renamed.</span></span>

## <a name="data-structures"></a><span data-ttu-id="93650-117">Structures de données</span><span class="sxs-lookup"><span data-stu-id="93650-117">Data Structures</span></span>

<span data-ttu-id="93650-118">Cette section décrit les types utilisés dans l' [exemple de fournisseur](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) que vous utilisez pour générer une instruction SQL.</span><span class="sxs-lookup"><span data-stu-id="93650-118">This section discusses the types used in the [Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) that you use to build a SQL statement.</span></span>

### <a name="isqlfragment"></a><span data-ttu-id="93650-119">ISqlFragment</span><span class="sxs-lookup"><span data-stu-id="93650-119">ISqlFragment</span></span>

<span data-ttu-id="93650-120">Cette section décrit les classes qui implémentent l'interface ISqlFragment, avec deux objectifs :</span><span class="sxs-lookup"><span data-stu-id="93650-120">This section covers the classes that implement the ISqlFragment interface, which serves two purposes:</span></span>

- <span data-ttu-id="93650-121">Type de retour commun à toutes les méthodes de visiteur.</span><span class="sxs-lookup"><span data-stu-id="93650-121">A common return type for all the visitor methods.</span></span>

- <span data-ttu-id="93650-122">Donne une méthode pour écrire la dernière chaîne SQL.</span><span class="sxs-lookup"><span data-stu-id="93650-122">Gives a method to write the final SQL string.</span></span>

```csharp
internal interface ISqlFragment {
   void WriteSql(SqlWriter writer, SqlGenerator sqlGenerator);
}
```

#### <a name="sqlbuilder"></a><span data-ttu-id="93650-123">SqlBuilder</span><span class="sxs-lookup"><span data-stu-id="93650-123">SqlBuilder</span></span>

<span data-ttu-id="93650-124">SqlBuilder est un périphérique de regroupement pour la dernière chaîne SQL, semblable à StringBuilder.</span><span class="sxs-lookup"><span data-stu-id="93650-124">SqlBuilder is a gathering device for the final SQL string, similar to StringBuilder.</span></span> <span data-ttu-id="93650-125">Il est constitué des chaînes qui composent le dernier SQL, avec des ISqlFragments qui peuvent être convertis en chaînes.</span><span class="sxs-lookup"><span data-stu-id="93650-125">It consists of the strings that make up the final SQL, along with ISqlFragments that can be converted into strings.</span></span>

```csharp
internal sealed class SqlBuilder : ISqlFragment {
   public void Append(object s)
   public void AppendLine()
   public bool IsEmpty
}
```

#### <a name="sqlselectstatement"></a><span data-ttu-id="93650-126">SqlSelectStatement</span><span class="sxs-lookup"><span data-stu-id="93650-126">SqlSelectStatement</span></span>

<span data-ttu-id="93650-127">SqlSelectStatement représente une instruction SQL SELECT canonique de la forme «SELECT...</span><span class="sxs-lookup"><span data-stu-id="93650-127">SqlSelectStatement represents a canonical SQL SELECT statement of the shape "SELECT …</span></span> <span data-ttu-id="93650-128">De..</span><span class="sxs-lookup"><span data-stu-id="93650-128">FROM  ..</span></span> <span data-ttu-id="93650-129">OÙ...</span><span class="sxs-lookup"><span data-stu-id="93650-129">WHERE …</span></span> <span data-ttu-id="93650-130">REGROUPER PAR...</span><span class="sxs-lookup"><span data-stu-id="93650-130">GROUP BY …</span></span> <span data-ttu-id="93650-131">TRIER PAR.</span><span class="sxs-lookup"><span data-stu-id="93650-131">ORDER BY".</span></span>

<span data-ttu-id="93650-132">Chacune des clauses SQL est représentée par un StringBuilder.</span><span class="sxs-lookup"><span data-stu-id="93650-132">Each of the SQL clauses is represented by a StringBuilder.</span></span> <span data-ttu-id="93650-133">De plus, il vérifie si Distinct a été spécifié et si l'instruction est au premier plan.</span><span class="sxs-lookup"><span data-stu-id="93650-133">In addition, it tracks whether Distinct has been specified and whether the statement is topmost.</span></span> <span data-ttu-id="93650-134">Si l'instruction n'est pas au premier plan, la clause ORDER BY est omise à moins que l'instruction ait également une clause TOP.</span><span class="sxs-lookup"><span data-stu-id="93650-134">If the statement is not topmost, the ORDER BY clause is omitted unless the statement also has a TOP clause.</span></span>

<span data-ttu-id="93650-135">FromExtents contient la liste des entrées de l'instruction SELECT.</span><span class="sxs-lookup"><span data-stu-id="93650-135">FromExtents contains the list of inputs for the SELECT statement.</span></span> <span data-ttu-id="93650-136">Habituellement il contient un seul élément.</span><span class="sxs-lookup"><span data-stu-id="93650-136">There is usually just one element in this.</span></span> <span data-ttu-id="93650-137">Les instructions SELECT pour les jointures peuvent temporairement avoir plusieurs éléments.</span><span class="sxs-lookup"><span data-stu-id="93650-137">SELECT statements for joins may temporarily have more than one element.</span></span>

<span data-ttu-id="93650-138">Si l'instruction SELECT est créée par un nœud de jointure, SqlSelectStatement maintient une liste de toutes les étendues aplanies dans la jointure dans AllJoinExtents.</span><span class="sxs-lookup"><span data-stu-id="93650-138">If the SELECT statement is created by a Join node, SqlSelectStatement maintains a list of all the extents that have been flattened in the join in AllJoinExtents.</span></span> <span data-ttu-id="93650-139">OuterExtents représente des références externes du SqlSelectStatement et est utilisé pour le changement de nom de l'alias de l'entrée.</span><span class="sxs-lookup"><span data-stu-id="93650-139">OuterExtents represents outer references of the SqlSelectStatement and is used for input alias renaming.</span></span>

```csharp
internal sealed class SqlSelectStatement : ISqlFragment {
   internal bool IsDistinct { get, set };
   internal bool IsTopMost

   internal List<Symbol> AllJoinExtents { get, set };
   internal List<Symbol> FromExtents { get};
   internal Dictionary<Symbol, bool> OuterExtents { get};

   internal TopClause Top { get, set };

   internal SqlBuilder Select {get};
   internal SqlBuilder From
   internal SqlBuilder Where
   internal SqlBuilder GroupBy
   public SqlBuilder OrderBy
}
```

#### <a name="topclause"></a><span data-ttu-id="93650-140">TopClause</span><span class="sxs-lookup"><span data-stu-id="93650-140">TopClause</span></span>

<span data-ttu-id="93650-141">TopClause représente l'expression TOP dans un SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="93650-141">TopClause represents the TOP expression in a SqlSelectStatement.</span></span> <span data-ttu-id="93650-142">La propriété TopCount indique le nombre de lignes TOP qui doivent être sélectionnées.</span><span class="sxs-lookup"><span data-stu-id="93650-142">The TopCount property indicates how many TOP rows should be selected.</span></span>  <span data-ttu-id="93650-143">Quand WithTies a la valeur true, la clause de la valeur est construite à partir d’un DbLimitExpression.</span><span class="sxs-lookup"><span data-stu-id="93650-143">When WithTies is true, the TopClause was built from a DbLimitExpression.</span></span>

```csharp
class TopClause : ISqlFragment {
   internal bool WithTies {get}
   internal ISqlFragment TopCount {get}
   internal TopClause(ISqlFragment topCount, bool withTies)
   internal TopClause(int topCount, bool withTies)
}
```

### <a name="symbols"></a><span data-ttu-id="93650-144">Symboles</span><span class="sxs-lookup"><span data-stu-id="93650-144">Symbols</span></span>

<span data-ttu-id="93650-145">Les classes associées au symbole et la table de symboles effectuent le changement de nom de l'alias de l'entrée, l'aplanissement de l'alias de jointure et le changement de nom de l'alias de colonne.</span><span class="sxs-lookup"><span data-stu-id="93650-145">The Symbol-related classes and the symbol table perform input alias renaming, join alias flattening, and column alias renaming.</span></span>

<span data-ttu-id="93650-146">La classe Symbol représente une étendue, une instruction SELECT imbriquée ou une colonne.</span><span class="sxs-lookup"><span data-stu-id="93650-146">The Symbol class represents an extent, a nested SELECT statement, or a column.</span></span> <span data-ttu-id="93650-147">Elle est utilisée à la place d'un alias réel pour autoriser le changement de nom après son utilisation et elle fournit également des informations supplémentaires pour l'artefact qu'elle représente (par exemple, le type).</span><span class="sxs-lookup"><span data-stu-id="93650-147">It is used instead of an actual alias to allow for renaming after it has been used and it also carries additional information for the artifact it represents (like the type).</span></span>

```csharp
class Symbol : ISqlFragment {
   internal Dictionary<string, Symbol> Columns {get}
   internal bool NeedsRenaming {get, set}
   internal bool IsUnnest {get, set}   //not used

   public string Name{get}
   public string NewName {get,set}
   internal TypeUsage Type {get, set}

   public Symbol(string name, TypeUsage type)
}
```

<span data-ttu-id="93650-148">Name stocke l'alias d'origine de l'étendue représentée, de l'instruction SELECT imbriquée ou d'une colonne.</span><span class="sxs-lookup"><span data-stu-id="93650-148">Name stores the original alias for the represented extent, nested SELECT statement, or a column.</span></span>

<span data-ttu-id="93650-149">NewName stocke l'alias qui sera utilisé dans l'instruction SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="93650-149">NewName stores the alias that will be used in the SQL SELECT statement.</span></span> <span data-ttu-id="93650-150">Il est initialement défini sur Name et renommé uniquement si nécessaire lors de la génération de la dernière requête de chaîne.</span><span class="sxs-lookup"><span data-stu-id="93650-150">It is originally set to Name, and only renamed if needed when generating the final string query.</span></span>

<span data-ttu-id="93650-151">Type est utile uniquement pour les symboles qui représentent des étendues et des instructions SELECT imbriquées.</span><span class="sxs-lookup"><span data-stu-id="93650-151">Type is only useful for symbols representing extents and nested SELECT statements.</span></span>

#### <a name="symbolpair"></a><span data-ttu-id="93650-152">SymbolPair</span><span class="sxs-lookup"><span data-stu-id="93650-152">SymbolPair</span></span>

<span data-ttu-id="93650-153">La classe SymbolPair résout un aplanissement d'enregistrement.</span><span class="sxs-lookup"><span data-stu-id="93650-153">The SymbolPair class addresses record flattening.</span></span>

<span data-ttu-id="93650-154">Considérez une expression de propriété D(v, "j3.j2.j1.a.x") où v est un VarRef, j1, j2, j3 sont des jointures, a est une étendue et x est une colonne.</span><span class="sxs-lookup"><span data-stu-id="93650-154">Consider a property expression D(v, "j3.j2.j1.a.x") where v is a VarRef, j1, j2, j3 are joins, a is an extent, and x is a columns.</span></span>

<span data-ttu-id="93650-155">Cela doit être traduit éventuellement en {j'}.{x'}.</span><span class="sxs-lookup"><span data-stu-id="93650-155">This has to be translated eventually into {j'}.{x'}.</span></span> <span data-ttu-id="93650-156">Le champ source représente le SqlStatement le plus à l'extérieur, qui représente une expression de jointure (soit j2), c'est toujours un symbole de jointure.</span><span class="sxs-lookup"><span data-stu-id="93650-156">The source field represents the outermost SqlStatement, representing a join expression (say j2); this is always a Join symbol.</span></span> <span data-ttu-id="93650-157">Le champ de colonne se déplace d'un symbole de jointure à un autre jusqu'à ce qu'il s'arrête à un symbole de non-jointure.</span><span class="sxs-lookup"><span data-stu-id="93650-157">The column field moves from one join symbol to the next until it stops at a non-join symbol.</span></span> <span data-ttu-id="93650-158">Cela est retourné lors de la visite d'un DbPropertyExpression mais n'est jamais ajouté à un SqlBuilder.</span><span class="sxs-lookup"><span data-stu-id="93650-158">This is returned when visiting a DbPropertyExpression but is never added to a SqlBuilder.</span></span>

```csharp
class SymbolPair : ISqlFragment {
   public Symbol Source;
   public Symbol Column;
   public SymbolPair(Symbol source, Symbol column)
}
```

#### <a name="joinsymbol"></a><span data-ttu-id="93650-159">JoinSymbol</span><span class="sxs-lookup"><span data-stu-id="93650-159">JoinSymbol</span></span>

<span data-ttu-id="93650-160">Un symbole de jointure est un symbole qui représente une instruction SELECT imbriquée avec une jointure ou une entrée de jointure.</span><span class="sxs-lookup"><span data-stu-id="93650-160">A Join symbol is a Symbol that represents a nested SELECT statement with a join or a join input.</span></span>

```csharp
internal sealed class JoinSymbol : Symbol {
   internal List<Symbol> ColumnList {get, set}
   internal List<Symbol> ExtentList {get}
   internal List<Symbol> FlattenedExtentList {get, set}
   internal Dictionary<string, Symbol> NameToExtent {get}
   internal bool IsNestedJoin {get, set}

   public JoinSymbol(string name, TypeUsage type, List<Symbol> extents)
}
```

<span data-ttu-id="93650-161">ColumnList représente la liste de colonnes dans la clause SELECT si ce symbole représente une instruction SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="93650-161">ColumnList represents the list of columns in the SELECT clause if this symbol represents a SQL SELECT statement.</span></span> <span data-ttu-id="93650-162">ExtentList est la liste des étendues dans la clause SELECT.</span><span class="sxs-lookup"><span data-stu-id="93650-162">ExtentList is the list of extents in the SELECT clause.</span></span> <span data-ttu-id="93650-163">Si la jointure a plusieurs étendues aplanies au niveau supérieur, FlattenedExtentList suit les étendues pour vérifier que les alias d'étendue sont renommés correctement.</span><span class="sxs-lookup"><span data-stu-id="93650-163">If the join has multiple extents flattened at the top level, FlattenedExtentList tracks the extents to ensure that extent aliases are renamed correctly.</span></span>

<span data-ttu-id="93650-164">NameToExtent possède toutes les étendues de ExtentList sous forme de dictionnaire.</span><span class="sxs-lookup"><span data-stu-id="93650-164">NameToExtent has all the extents in ExtentList as a dictionary.</span></span> <span data-ttu-id="93650-165">IsNestedJoin est utilisé pour déterminer si un JoinSymbol est un symbole de jointure ordinaire ou s'il possède un SqlSelectStatement correspondant.</span><span class="sxs-lookup"><span data-stu-id="93650-165">IsNestedJoin is used to determine whether a JoinSymbol is an ordinary join symbol or one that has a corresponding SqlSelectStatement.</span></span>

<span data-ttu-id="93650-166">Toutes les listes sont définies exactement une fois puis utilisées pour les recherches ou l'énumération.</span><span class="sxs-lookup"><span data-stu-id="93650-166">All the lists are set exactly once and then used for lookups or enumeration.</span></span>

#### <a name="symboltable"></a><span data-ttu-id="93650-167">SymbolTable</span><span class="sxs-lookup"><span data-stu-id="93650-167">SymbolTable</span></span>

<span data-ttu-id="93650-168">SymbolTable est utilisé pour résoudre des noms de variable en symboles.</span><span class="sxs-lookup"><span data-stu-id="93650-168">SymbolTable is used to resolve variable names to Symbols.</span></span> <span data-ttu-id="93650-169">SymbolTable est implémenté en tant que pile avec une nouvelle entrée pour chaque étendue.</span><span class="sxs-lookup"><span data-stu-id="93650-169">SymbolTable is implemented as a stack with a new entry for each scope.</span></span> <span data-ttu-id="93650-170">Les recherches s'effectuent du haut de la pile vers le bas jusqu'à ce qu'une entrée soit trouvée.</span><span class="sxs-lookup"><span data-stu-id="93650-170">Lookups search from the top of the stack to the bottom until an entry is found.</span></span>

```csharp
internal sealed class SymbolTable {
   internal void EnterScope()
   internal void ExitScope()
   internal void Add(string name, Symbol value)
   internal Symbol Lookup(string name)
}
```

<span data-ttu-id="93650-171">Il y a seulement un SymbolTable par instance du module de génération SQL.</span><span class="sxs-lookup"><span data-stu-id="93650-171">There is only one SymbolTable per one instance of the Sql Generation module.</span></span> <span data-ttu-id="93650-172">Les étendues sont entrées et sorties pour chaque nœud relationnel.</span><span class="sxs-lookup"><span data-stu-id="93650-172">Scopes are entered and exited for each relational node.</span></span> <span data-ttu-id="93650-173">Tous les symboles des premières étendues sont visibles aux étendues ultérieures à moins d'être masqués par d'autres symboles avec le même nom.</span><span class="sxs-lookup"><span data-stu-id="93650-173">All symbols in earlier scopes are visible to later scopes unless hidden by other symbols with the same name.</span></span>

### <a name="global-state-for-the-visitor"></a><span data-ttu-id="93650-174">État général du visiteur</span><span class="sxs-lookup"><span data-stu-id="93650-174">Global State for the Visitor</span></span>

<span data-ttu-id="93650-175">Pour aider au changement de nom des alias et des colonnes, maintenez une liste de tous les noms de colonne (AllColumnNames) et des alias d’étendue (AllExtentNames) utilisés dans le premier passage sur l’arborescence de requêtes.</span><span class="sxs-lookup"><span data-stu-id="93650-175">To assist in renaming of aliases and columns, maintain a list of all the column names (AllColumnNames) and extent aliases (AllExtentNames) that have been used in the first pass over the query tree.</span></span>  <span data-ttu-id="93650-176">La table de symboles résout des noms de variable en des symboles.</span><span class="sxs-lookup"><span data-stu-id="93650-176">The symbol table resolves variable names to Symbols.</span></span> <span data-ttu-id="93650-177">IsVarRefSingle est utilisé uniquement à des fins de vérification, il n'est pas strictement nécessaire.</span><span class="sxs-lookup"><span data-stu-id="93650-177">IsVarRefSingle is only used for verification purposes, it is not strictly necessary.</span></span>

<span data-ttu-id="93650-178">Les deux piles utilisées via CurrentSelectStatement et IsParentAJoin permettent de passer des « paramètres » des nœuds parents aux nœuds enfants, puisque le modèle visiteur ne nous permet pas de passer des paramètres.</span><span class="sxs-lookup"><span data-stu-id="93650-178">The two stacks used via CurrentSelectStatement and IsParentAJoin are used to pass "parameters" from parent to child nodes, since the visitor pattern does not allow us to pass parameters.</span></span>

```csharp
internal Dictionary<string, int> AllExtentNames {get}
internal Dictionary<string, int> AllColumnNames {get}
SymbolTable symbolTable = new SymbolTable();
bool isVarRefSingle = false;

Stack<SqlSelectStatement> selectStatementStack;
private SqlSelectStatement CurrentSelectStatement{get}

Stack<bool> isParentAJoinStack;
private bool IsParentAJoin{get}
```

## <a name="common-scenarios"></a><span data-ttu-id="93650-179">Scénarios courants</span><span class="sxs-lookup"><span data-stu-id="93650-179">Common Scenarios</span></span>

<span data-ttu-id="93650-180">Cette section décrit des scénarios de fournisseur communs.</span><span class="sxs-lookup"><span data-stu-id="93650-180">This section discusses common provider scenarios.</span></span>

### <a name="grouping-expression-nodes-into-sql-statements"></a><span data-ttu-id="93650-181">Regroupement de nœuds d'expression dans les Instructions SQL</span><span class="sxs-lookup"><span data-stu-id="93650-181">Grouping Expression Nodes into SQL Statements</span></span>

<span data-ttu-id="93650-182">Un SqlSelectStatement est créé lorsque le premier nœud relationnel est rencontré (en général une étendue DbScanExpression) lors de la visite de l’arborescence de bas en haut.</span><span class="sxs-lookup"><span data-stu-id="93650-182">A SqlSelectStatement is created when the first relational node is encountered (typically a DbScanExpression extent) when visiting the tree from the bottom up.</span></span> <span data-ttu-id="93650-183">Pour produire une instruction SQL SELECT avec le moins possible de requêtes imbriquées, regroupez le plus possible de ses nœuds parents dans ce SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="93650-183">To produce a SQL SELECT statement with as few nested queries as possible, aggregate as many of its parent nodes as possible in that SqlSelectStatement.</span></span>

<span data-ttu-id="93650-184">La décision qui permet de savoir si un nœud (relationnel) donné peut être ajouté au SqlSelectStatement actuel (celui qui est retourné lors de la visite de l'entrée) ou si une nouvelle instruction doit être démarrée, est prise par la méthode IsCompatible et dépend de ce qui se trouve déjà dans le SqlSelectStatement, ce qui dépend des nœuds situés sous le nœud donné.</span><span class="sxs-lookup"><span data-stu-id="93650-184">The decision of whether a given (relational) node can be added to the current SqlSelectStatement (the one returned when visiting the input) or if a new statement needs to be started is computed by the method IsCompatible and depends on what is already in the SqlSelectStatement, which depends on what nodes were below the given node.</span></span>

<span data-ttu-id="93650-185">En général, si les clauses d'instruction SQL sont évaluées après des clauses où les nœuds considérés pour la fusion ne sont pas vides, le nœud ne peut pas être ajouté à l'instruction actuelle.</span><span class="sxs-lookup"><span data-stu-id="93650-185">Typically, if SQL statement clauses are evaluated after clauses where the nodes being considered for merging are not empty, the node cannot be added to the current statement.</span></span> <span data-ttu-id="93650-186">Par exemple, si le nœud suivant est un filtre, ce nœud peut être incorporé dans le SqlSelectStatement actuel seulement si ce qui suit a la valeur true :</span><span class="sxs-lookup"><span data-stu-id="93650-186">For example, if the next node is a Filter, that node can be incorporated into the current SqlSelectStatement only if the following is true:</span></span>

- <span data-ttu-id="93650-187">La liste SELECT est vide.</span><span class="sxs-lookup"><span data-stu-id="93650-187">The SELECT list is empty.</span></span> <span data-ttu-id="93650-188">Si la liste SELECT n'est pas vide, la liste de sélection a été produite par un nœud qui précède le filtre et le prédicat peut faire référence aux colonnes produites par cette liste SELECT.</span><span class="sxs-lookup"><span data-stu-id="93650-188">If the SELECT list is not empty, the select list was produced by a node preceding the filter and the predicate may refer to columns produced by that SELECT list.</span></span>

- <span data-ttu-id="93650-189">Le GROUPBY est vide.</span><span class="sxs-lookup"><span data-stu-id="93650-189">The GROUPBY is empty.</span></span> <span data-ttu-id="93650-190">Si le GROUPBY n'est pas vide, l'ajout du filtre signifierait filtrer avant de grouper, ce qui n'est pas correct.</span><span class="sxs-lookup"><span data-stu-id="93650-190">If the GROUPBY is not empty, adding the filter would mean filtering before grouping, which is not correct.</span></span>

- <span data-ttu-id="93650-191">La clause TOP est vide.</span><span class="sxs-lookup"><span data-stu-id="93650-191">The TOP clause is empty.</span></span> <span data-ttu-id="93650-192">Si la clause TOP n'est pas vide, l'ajout du filtre signifierait filtrer avant d'effectuer TOP, ce qui n'est pas correct.</span><span class="sxs-lookup"><span data-stu-id="93650-192">If the TOP clause is not empty, adding the filter would mean filtering before doing TOP, which is not correct.</span></span>

<span data-ttu-id="93650-193">Cela ne s'applique pas aux nœuds non relationnels comme DbConstantExpression ou des expressions arithmétiques, parce que ceux-ci sont toujours inclus dans le cadre d'un SqlSelectStatement existant.</span><span class="sxs-lookup"><span data-stu-id="93650-193">This does not apply to non-relational nodes like DbConstantExpression or arithmetic expressions, because these are always included as part of an existing SqlSelectStatement.</span></span>

<span data-ttu-id="93650-194">De même, lorsque la racine de l'arborescence de jointure est rencontrée (un nœud de jointure qui n'a pas de parent de jointure), un nouveau SqlSelectStatement est démarré.</span><span class="sxs-lookup"><span data-stu-id="93650-194">Also, when encountering the root of join tree (a join node that does not have a join parent), a new SqlSelectStatement is started.</span></span> <span data-ttu-id="93650-195">Tous ses enfants de la jointure externe à gauche sont regroupés dans ce SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="93650-195">All of its left spine join children are aggregated into that SqlSelectStatement.</span></span>

<span data-ttu-id="93650-196">Lorsqu'un nouveau SqlSelectStatement est démarré et que l'actuel est ajouté à l'entrée, le SqlSelectStatement actuel peut devoir être complété en ajoutant des colonnes de projection (clause SELECT) s'il n'y en a pas.</span><span class="sxs-lookup"><span data-stu-id="93650-196">Whenever a new SqlSelectStatement is started, and the current one is added to the input, the current SqlSelectStatement may need to be completed by adding projection columns (a SELECT clause) if one does not exist.</span></span> <span data-ttu-id="93650-197">Cela est effectué avec la méthode AddDefaultColumns qui regarde les FromExtents du SqlSelectStatement et ajoute à la liste des colonnes projetées toutes les colonnes que la liste d'étendues représentée par FromExtents apporte à l'étendue.</span><span class="sxs-lookup"><span data-stu-id="93650-197">This is done with the method AddDefaultColumns, which looks at the FromExtents of the SqlSelectStatement and adds all the columns that the list of extents represented by FromExtents brings in scope to the list of projected columns.</span></span> <span data-ttu-id="93650-198">Cela est effectué parce qu'à ce stade, on ne sait pas quelles colonnes sont référencées par les autres nœuds.</span><span class="sxs-lookup"><span data-stu-id="93650-198">This is done, because at that point, it is unknown which columns are referenced by the other nodes.</span></span> <span data-ttu-id="93650-199">Cela peut être optimisé pour projeter uniquement les colonnes qui peuvent être utilisées ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="93650-199">This can be optimized to only project the columns that can later be used.</span></span>

### <a name="join-flattening"></a><span data-ttu-id="93650-200">Aplanissement de jointure</span><span class="sxs-lookup"><span data-stu-id="93650-200">Join Flattening</span></span>

<span data-ttu-id="93650-201">La propriété IsParentAJoin aide à déterminer si une jointure donnée peut être aplanie.</span><span class="sxs-lookup"><span data-stu-id="93650-201">The IsParentAJoin property helps determine whether a given join can be flattened.</span></span> <span data-ttu-id="93650-202">En particulier, IsParentAJoin retourne uniquement la valeur `true` pour l'enfant gauche d'une jointure et pour chaque DbScanExpression qui est une entrée immédiate à une jointure, dans ce cas le nœud enfant réutilise le même SqlSelectStatement qui peut être utilisé ultérieurement par le parent.</span><span class="sxs-lookup"><span data-stu-id="93650-202">In particular, IsParentAJoin returns `true` only for the left child of a join and for each DbScanExpression that is an immediate input to a join, in which case that child node reuses the same SqlSelectStatement that the parent would later use.</span></span> <span data-ttu-id="93650-203">Pour plus d'informations, consultez « Expressions de jointure ».</span><span class="sxs-lookup"><span data-stu-id="93650-203">For more information, see "Join Expressions".</span></span>

### <a name="input-alias-redirecting"></a><span data-ttu-id="93650-204">Redirection d'alias d'entrée</span><span class="sxs-lookup"><span data-stu-id="93650-204">Input Alias Redirecting</span></span>

<span data-ttu-id="93650-205">La redirection d'alias d'entrée est accomplie avec la table de symboles.</span><span class="sxs-lookup"><span data-stu-id="93650-205">Input alias redirecting is accomplished with the symbol table.</span></span>

<span data-ttu-id="93650-206">Pour expliquer la redirection d’alias d’entrée, reportez-vous au premier exemple de la rubrique [génération de SQL à partir d’arborescences de commandes-meilleures pratiques](generating-sql-from-command-trees-best-practices.md).</span><span class="sxs-lookup"><span data-stu-id="93650-206">To explain input alias redirecting, refer to the first example in [Generating SQL from Command Trees - Best Practices](generating-sql-from-command-trees-best-practices.md).</span></span>  <span data-ttu-id="93650-207">Dans cet exemple « a » doit être redirigé vers « b » dans la projection.</span><span class="sxs-lookup"><span data-stu-id="93650-207">There "a" needed to be redirected to "b" in the projection.</span></span>

<span data-ttu-id="93650-208">Lorsqu'un objet SqlSelectStatement est créé, l'étendue qui est l'entrée du nœud est mise dans la propriété FROM du SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="93650-208">When a SqlSelectStatement object is created, the extent that is the input to the node is put in the From property of the SqlSelectStatement.</span></span> <span data-ttu-id="93650-209">Un symbole (\<symbol_b >) est créé en fonction du nom de liaison d’entrée (« b ») pour représenter cette étendue et « AS » + \<symbol_b > est ajouté à la clause from.</span><span class="sxs-lookup"><span data-stu-id="93650-209">A Symbol (\<symbol_b>) is created based on the input binding name ("b") to represent that extent and "AS  " + \<symbol_b> is appended to the From Clause.</span></span>  <span data-ttu-id="93650-210">Le symbole est également ajouté à la propriété FromExtents.</span><span class="sxs-lookup"><span data-stu-id="93650-210">The symbol is also added to the FromExtents property.</span></span>

<span data-ttu-id="93650-211">Le symbole est également ajouté à la table de symboles pour lier le nom de liaison d’entrée à celui-ci (« b », \<symbol_b >).</span><span class="sxs-lookup"><span data-stu-id="93650-211">The symbol is also added to the symbol table to link the input binding name to it ("b", \<symbol_b>).</span></span>

<span data-ttu-id="93650-212">Si un nœud suivant réutilise ce SqlSelectStatement, il ajoute une entrée à la table de symboles pour lier son nom de liaison d’entrée à ce symbole.</span><span class="sxs-lookup"><span data-stu-id="93650-212">If a subsequent node reuses that SqlSelectStatement, it adds an entry to the symbol table to link its input binding name to that symbol.</span></span> <span data-ttu-id="93650-213">Dans notre exemple, le DbProjectExpression avec le nom de liaison d’entrée « a » réutiliserait le SqlSelectStatement et ajoutera (« a », \< symbol_b >) à la table.</span><span class="sxs-lookup"><span data-stu-id="93650-213">In our example, the DbProjectExpression with the input binding name of "a" would reuse the SqlSelectStatement and add ("a", \< symbol_b>) to the table.</span></span>

<span data-ttu-id="93650-214">Lorsque les expressions référencent le nom de liaison d’entrée du nœud qui réutilise le SqlSelectStatement, cette référence est résolue à l’aide de la table de symboles en symbole correct redirigé.</span><span class="sxs-lookup"><span data-stu-id="93650-214">When expressions reference the input binding name of the node that is reusing the SqlSelectStatement, that reference is resolved using the symbol table to the correct redirected symbol.</span></span> <span data-ttu-id="93650-215">Lorsque « a » de « a. x » est résolu lors de la visite du DbVariableReferenceExpression représentant « a », il se résout en symbole \<symbol_b >.</span><span class="sxs-lookup"><span data-stu-id="93650-215">When "a" from "a.x" is resolved while visiting the DbVariableReferenceExpression representing "a" it will resolve to the Symbol \<symbol_b>.</span></span>

### <a name="join-alias-flattening"></a><span data-ttu-id="93650-216">Aplanissement d'alias de jointure</span><span class="sxs-lookup"><span data-stu-id="93650-216">Join Alias Flattening</span></span>

<span data-ttu-id="93650-217">L'aplanissement d'alias de jointure est accompli lors de la visite d'un DbPropertyExpression comme décrit dans la section intitulée DbPropertyExpression.</span><span class="sxs-lookup"><span data-stu-id="93650-217">Join alias flattening is achieved when visiting a DbPropertyExpression as described in the section titled DbPropertyExpression.</span></span>

### <a name="column-name-and-extent-alias-renaming"></a><span data-ttu-id="93650-218">Changement du nom de colonne et du nom d'alias d'étendue</span><span class="sxs-lookup"><span data-stu-id="93650-218">Column Name and Extent Alias Renaming</span></span>

<span data-ttu-id="93650-219">Le problème du changement du nom de colonne et du nom d'alias d'étendue est résolu à l'aide de symboles qui sont uniquement remplacés par des alias dans la deuxième phase de la génération décrite dans la section intitulée Deuxième phase de la génération SQL : génération de la commande de chaîne.</span><span class="sxs-lookup"><span data-stu-id="93650-219">The issue of column name and extent alias renaming is addressed by using symbols that only get substituted with aliases in the second phase of the generation described in the section titled Second Phase of SQL Generation: Generating the String Command.</span></span>

## <a name="first-phase-of-the-sql-generation-visiting-the-expression-tree"></a><span data-ttu-id="93650-220">Première phase de la génération SQL : visite de l’arborescence de l’expression</span><span class="sxs-lookup"><span data-stu-id="93650-220">First Phase of the SQL Generation: Visiting the Expression Tree</span></span>

<span data-ttu-id="93650-221">Cette section décrit la première phase de génération SQL, lorsque l'expression qui représente la requête est visitée et qu'une structure intermédiaire est produite, telle qu'un SqlSelectStatement ou un SqlBuilder.</span><span class="sxs-lookup"><span data-stu-id="93650-221">This section describes the first phase of SQL generation, when the expression representing the query is visited and an intermediate structure is produced, either a SqlSelectStatement or a SqlBuilder.</span></span>

<span data-ttu-id="93650-222">Cette section décrit les principes de la visite de catégories de nœud d'expression différentes et les détails de la visite des types d'expression spécifiques.</span><span class="sxs-lookup"><span data-stu-id="93650-222">This section describes the principles of visiting different expression node categories, and details of visiting specific expression types.</span></span>

### <a name="relational-non-join-nodes"></a><span data-ttu-id="93650-223">Nœuds relationnels (non-jointure)</span><span class="sxs-lookup"><span data-stu-id="93650-223">Relational (Non-Join) Nodes</span></span>

<span data-ttu-id="93650-224">Les types d'expression suivants prennent en charge les nœuds de non-jointure :</span><span class="sxs-lookup"><span data-stu-id="93650-224">The following expression types support non-join nodes:</span></span>

- <span data-ttu-id="93650-225">DbDistinctExpression</span><span class="sxs-lookup"><span data-stu-id="93650-225">DbDistinctExpression</span></span>

- <span data-ttu-id="93650-226">DbFilterExpression</span><span class="sxs-lookup"><span data-stu-id="93650-226">DbFilterExpression</span></span>

- <span data-ttu-id="93650-227">DbGroupByExpression</span><span class="sxs-lookup"><span data-stu-id="93650-227">DbGroupByExpression</span></span>

- <span data-ttu-id="93650-228">DbLimitExpression</span><span class="sxs-lookup"><span data-stu-id="93650-228">DbLimitExpression</span></span>

- <span data-ttu-id="93650-229">DbProjectExpression</span><span class="sxs-lookup"><span data-stu-id="93650-229">DbProjectExpression</span></span>

- <span data-ttu-id="93650-230">DbSkipExpression</span><span class="sxs-lookup"><span data-stu-id="93650-230">DbSkipExpression</span></span>

- <span data-ttu-id="93650-231">DbSortExpression</span><span class="sxs-lookup"><span data-stu-id="93650-231">DbSortExpression</span></span>

<span data-ttu-id="93650-232">La visite de ces nœuds suit le modèle suivant :</span><span class="sxs-lookup"><span data-stu-id="93650-232">Visiting these nodes follows the following pattern:</span></span>

1. <span data-ttu-id="93650-233">Visitez l'entrée relationnelle et obtenez le SqlSelectStatement qui en résulte.</span><span class="sxs-lookup"><span data-stu-id="93650-233">Visit the relational input and get the resulting SqlSelectStatement.</span></span> <span data-ttu-id="93650-234">L'entrée à un nœud relationnel peut être l'un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="93650-234">The input to a relational node could be one of the following:</span></span>

    - <span data-ttu-id="93650-235">Un nœud relationnel, notamment une étendue (DbScanExpression, par exemple).</span><span class="sxs-lookup"><span data-stu-id="93650-235">A relational node, including an extent (a DbScanExpression, for example).</span></span> <span data-ttu-id="93650-236">La visite d'un tel nœud retourne un SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="93650-236">Visiting such a node returns a SqlSelectStatement.</span></span>

    - <span data-ttu-id="93650-237">Une expression d'opération Set (UNION ALL, par exemple).</span><span class="sxs-lookup"><span data-stu-id="93650-237">A set operation expression (UNION ALL, for example).</span></span> <span data-ttu-id="93650-238">Le résultat doit être mis entre parenthèses et placé dans la clause FROM d'un nouveau SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="93650-238">The result has to be wrapped in brackets and put in the FROM clause of a new SqlSelectStatement.</span></span>

2. <span data-ttu-id="93650-239">Vérifiez si le nœud actuel peut être ajouté au SqlSelectStatement produit par l'entrée.</span><span class="sxs-lookup"><span data-stu-id="93650-239">Check whether the current node can be added to the SqlSelectStatement produced by the input.</span></span> <span data-ttu-id="93650-240">La section intitulée Regroupement d'expressions dans des instructions SQL décrit ceci.</span><span class="sxs-lookup"><span data-stu-id="93650-240">The section titled Grouping Expressions into SQL Statements describes this.</span></span> <span data-ttu-id="93650-241">Dans le cas contraire,</span><span class="sxs-lookup"><span data-stu-id="93650-241">If not,</span></span>

    - <span data-ttu-id="93650-242">Dépilez l'objet SqlSelectStatement actuel.</span><span class="sxs-lookup"><span data-stu-id="93650-242">Pop the current SqlSelectStatement object.</span></span>

    - <span data-ttu-id="93650-243">Créez un objet SqlSelectStatement et ajoutez le SqlSelectStatement dépilé en tant que FROM du nouvel objet SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="93650-243">Create a new SqlSelectStatement object and add the popped SqlSelectStatement as the FROM of the new SqlSelectStatement object.</span></span>

    - <span data-ttu-id="93650-244">Mettez le nouvel objet sur la pile.</span><span class="sxs-lookup"><span data-stu-id="93650-244">Put the new object on top of the stack.</span></span>

3. <span data-ttu-id="93650-245">Redirigez la liaison de l’expression d’entrée vers le symbole correct de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="93650-245">Redirect the input expression binding to the correct symbol from the input.</span></span> <span data-ttu-id="93650-246">Ces informations sont maintenues dans l'objet SqlSelectStatement.</span><span class="sxs-lookup"><span data-stu-id="93650-246">This information is maintained in the SqlSelectStatement object.</span></span>

4. <span data-ttu-id="93650-247">Ajoutez une nouvelle étendue SymbolTable.</span><span class="sxs-lookup"><span data-stu-id="93650-247">Add a new SymbolTable scope.</span></span>

5. <span data-ttu-id="93650-248">Visitez la partie non-entrée de l’expression (par exemple, projection et prédicat).</span><span class="sxs-lookup"><span data-stu-id="93650-248">Visit the non-input part of the expression (for example, Projection and Predicate).</span></span>

6. <span data-ttu-id="93650-249">Dépilez tous les objets ajoutés aux piles globales.</span><span class="sxs-lookup"><span data-stu-id="93650-249">Pop all the objects added to the global stacks.</span></span>

 <span data-ttu-id="93650-250">DbSkipExpression n'a pas d'équivalent direct dans SQL.</span><span class="sxs-lookup"><span data-stu-id="93650-250">DbSkipExpression not have a direct equivalent in SQL.</span></span> <span data-ttu-id="93650-251">Logiquement, il est traduit par :</span><span class="sxs-lookup"><span data-stu-id="93650-251">Logically, it is translated into:</span></span>

```sql
SELECT Y.x1, Y.x2, ..., Y.xn
FROM (
   SELECT X.x1, X.x2, ..., X.xn, row_number() OVER (ORDER BY sk1, sk2, ...) AS [row_number]
   FROM input as X
   ) as Y
WHERE Y.[row_number] > count
ORDER BY sk1, sk2, ...
```

### <a name="join-expressions"></a><span data-ttu-id="93650-252">Expressions de jointure</span><span class="sxs-lookup"><span data-stu-id="93650-252">Join Expressions</span></span>

<span data-ttu-id="93650-253">Les éléments suivants sont considérés comme des expressions de jointure et sont traités de manière commune par la méthode VisitJoinExpression :</span><span class="sxs-lookup"><span data-stu-id="93650-253">The following are considered join expressions and they are processed in a common way, by the VisitJoinExpression method:</span></span>

- <span data-ttu-id="93650-254">DbApplyExpression</span><span class="sxs-lookup"><span data-stu-id="93650-254">DbApplyExpression</span></span>

- <span data-ttu-id="93650-255">DbJoinExpression</span><span class="sxs-lookup"><span data-stu-id="93650-255">DbJoinExpression</span></span>

- <span data-ttu-id="93650-256">DbCrossJoinExpression</span><span class="sxs-lookup"><span data-stu-id="93650-256">DbCrossJoinExpression</span></span>

<span data-ttu-id="93650-257">Voici les étapes de la visite :</span><span class="sxs-lookup"><span data-stu-id="93650-257">The following are the visit steps:</span></span>

<span data-ttu-id="93650-258">En premier lieu, avant de visiter les enfants, IsParentAJoin est appelé pour vérifier si le nœud de jointure est un enfant d'une jointure le long d'une colonne vertébrale gauche.</span><span class="sxs-lookup"><span data-stu-id="93650-258">First, before visiting the children, IsParentAJoin is invoked to check whether the join node is a child of a join along a left spine.</span></span> <span data-ttu-id="93650-259">S'il retourne la valeur false, un nouveau SqlSelectStatement est démarré.</span><span class="sxs-lookup"><span data-stu-id="93650-259">If it returns false, a new SqlSelectStatement is started.</span></span> <span data-ttu-id="93650-260">Dans ce sens, les jointures sont visitées de manière différente du reste des nœuds, puisque le parent (le nœud de jointure) crée le SqlSelectStatement pour que les enfants puissent l'utiliser.</span><span class="sxs-lookup"><span data-stu-id="93650-260">In that sense, joins are visited differently from the rest of the nodes, as the parent (the join node) creates the SqlSelectStatement for the children to possibly use.</span></span>

<span data-ttu-id="93650-261">Deuxièmement, traitez les entrées une par une.</span><span class="sxs-lookup"><span data-stu-id="93650-261">Second, process the inputs one at a time.</span></span> <span data-ttu-id="93650-262">Pour chaque entrée :</span><span class="sxs-lookup"><span data-stu-id="93650-262">For each input:</span></span>

1. <span data-ttu-id="93650-263">Visitez l'entrée.</span><span class="sxs-lookup"><span data-stu-id="93650-263">Visit the input.</span></span>

2. <span data-ttu-id="93650-264">Post-traitez le résultat de la visite de l'entrée en appelant ProcessJoinInputResult qui doit maintenir la table de symboles après avoir visité un enfant d'une expression de jointure et peut terminer le SqlSelectStatement produit par l'enfant.</span><span class="sxs-lookup"><span data-stu-id="93650-264">Post process the result of visiting the input by invoking ProcessJoinInputResult, which is responsible for maintaining the symbol table after visiting a child of a join expression and possibly finishing the SqlSelectStatement produced by the child.</span></span> <span data-ttu-id="93650-265">Le résultat de l'enfant peut être l'un des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="93650-265">The child's result could be one of the following:</span></span>

    - <span data-ttu-id="93650-266">Un SqlSelectStatement différent de celui auquel le parent est ajouté.</span><span class="sxs-lookup"><span data-stu-id="93650-266">A SqlSelectStatement different from the one to which the parent will be added.</span></span> <span data-ttu-id="93650-267">Dans ce cas, il peut devoir être complété en ajoutant des colonnes par défaut.</span><span class="sxs-lookup"><span data-stu-id="93650-267">In such case, it may need to be completed by adding default columns.</span></span> <span data-ttu-id="93650-268">Si l'entrée est une jointure, vous devez créer un symbole de jointure.</span><span class="sxs-lookup"><span data-stu-id="93650-268">If the input was a Join, you need to create a new join symbol.</span></span> <span data-ttu-id="93650-269">Dans le cas contraire, créez un symbole normal.</span><span class="sxs-lookup"><span data-stu-id="93650-269">Otherwise, create a normal symbol.</span></span>

    - <span data-ttu-id="93650-270">Une étendue (DbScanExpression, par exemple), auquel cas il est simplement ajouté à la liste d'entrées du SqlSelectStatement du parent.</span><span class="sxs-lookup"><span data-stu-id="93650-270">An extent (a DbScanExpression, for example), in which case it is simply added to the list of inputs of the parent’s SqlSelectStatement.</span></span>

    - <span data-ttu-id="93650-271">Différent d'un SqlSelectStatement, auquel cas il est mis entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="93650-271">Not a SqlSelectStatement, in which case it is wrapped with brackets.</span></span>

    - <span data-ttu-id="93650-272">Le même SqlSelectStatement auquel le parent est ajouté.</span><span class="sxs-lookup"><span data-stu-id="93650-272">The same SqlSelectStatement to which the parent is added.</span></span> <span data-ttu-id="93650-273">Dans ce cas, les symboles de la liste FromExtents doivent être remplacés par un nouveau JoinSymbol unique qui les représente tous.</span><span class="sxs-lookup"><span data-stu-id="93650-273">In such case, the symbols in the FromExtents list need to be replaced with a single new JoinSymbol representing them all.</span></span>

    - <span data-ttu-id="93650-274">Dans les trois premiers cas, AddFromSymbol est appelé pour ajouter la clause AS et mettre à jour la table de symboles.</span><span class="sxs-lookup"><span data-stu-id="93650-274">For the first three cases, AddFromSymbol is called to add the AS clause, and update the symbol table.</span></span>

<span data-ttu-id="93650-275">Troisièmement, la condition de jointure (s'il y en a une) est visitée.</span><span class="sxs-lookup"><span data-stu-id="93650-275">Third, the join condition (if any) is visited.</span></span>

### <a name="set-operations"></a><span data-ttu-id="93650-276">Opérations ensemblistes</span><span class="sxs-lookup"><span data-stu-id="93650-276">Set Operations</span></span>

<span data-ttu-id="93650-277">Les opérations Set DbUnionAllExpression, DbExceptExpression et DbIntersectExpression sont traitées par la méthode VisitSetOpExpression.</span><span class="sxs-lookup"><span data-stu-id="93650-277">The set operations DbUnionAllExpression, DbExceptExpression, and DbIntersectExpression are processed by the method VisitSetOpExpression.</span></span> <span data-ttu-id="93650-278">Elle crée un SqlBuilder de la forme</span><span class="sxs-lookup"><span data-stu-id="93650-278">It creates a SqlBuilder of the shape</span></span>

```xml
<leftSqlSelectStatement> <setOp> <rightSqlSelectStatement>
```

<span data-ttu-id="93650-279">Lorsque \<leftSqlSelectStatement > et \<rightSqlSelectStatement > sont SqlSelectStatements obtenus en visitant chacune des entrées, et \<setOp > est l’opération correspondante (UNION ALL par exemple).</span><span class="sxs-lookup"><span data-stu-id="93650-279">Where \<leftSqlSelectStatement> and \<rightSqlSelectStatement> are SqlSelectStatements obtained by visiting each of the inputs, and \<setOp> is the corresponding operation (UNION ALL for example).</span></span>

### <a name="dbscanexpression"></a><span data-ttu-id="93650-280">DbScanExpression</span><span class="sxs-lookup"><span data-stu-id="93650-280">DbScanExpression</span></span>

<span data-ttu-id="93650-281">S'il est visité dans un contexte de jointure (comme une entrée à une jointure qui est un enfant gauche d'une autre jointure), DbScanExpression retourne un SqlBuilder avec le SQL cible pour la cible correspondante, qui peut être une requête de définition, une table ou une vue.</span><span class="sxs-lookup"><span data-stu-id="93650-281">If visited in a join context (as an input to a join that is a left child of another join), DbScanExpression returns a SqlBuilder with the target SQL for the corresponding target, which is either a defining query, table, or a view.</span></span> <span data-ttu-id="93650-282">Dans le cas contraire, un nouveau SqlSelectStatement est créé avec le champ FROM défini pour correspondre à la cible correspondante.</span><span class="sxs-lookup"><span data-stu-id="93650-282">Otherwise, a new SqlSelectStatement is created with the FROM field set to correspond to the corresponding target.</span></span>

### <a name="dbvariablereferenceexpression"></a><span data-ttu-id="93650-283">DbVariableReferenceExpression</span><span class="sxs-lookup"><span data-stu-id="93650-283">DbVariableReferenceExpression</span></span>

<span data-ttu-id="93650-284">La visite d'un DbVariableReferenceExpression retourne le symbole qui correspond à cette expression de référence de variable selon une recherche dans la table de symboles.</span><span class="sxs-lookup"><span data-stu-id="93650-284">The visit of a DbVariableReferenceExpression returns the Symbol corresponding to that variable reference expression based on a look up in the symbol table.</span></span>

### <a name="dbpropertyexpression"></a><span data-ttu-id="93650-285">DbPropertyExpression</span><span class="sxs-lookup"><span data-stu-id="93650-285">DbPropertyExpression</span></span>

<span data-ttu-id="93650-286">L'aplanissement d'alias de jointure est identifié et traité lors de la visite d'un DbPropertyExpression.</span><span class="sxs-lookup"><span data-stu-id="93650-286">Join alias flattening is identified and processed when visiting a DbPropertyExpression.</span></span>

<span data-ttu-id="93650-287">La propriété Instance est visitée en premier et le résultat est un symbole, un JoinSymbol ou un SymbolPair.</span><span class="sxs-lookup"><span data-stu-id="93650-287">The Instance property is first visited and the result is a Symbol, a JoinSymbol, or a SymbolPair.</span></span> <span data-ttu-id="93650-288">Voici comment ces trois cas sont gérés :</span><span class="sxs-lookup"><span data-stu-id="93650-288">Here is how these three cases are handled:</span></span>

- <span data-ttu-id="93650-289">Si un JoinSymbol est retourné, alors sa propriété NameToExtent contient un symbole pour la propriété nécessaire.</span><span class="sxs-lookup"><span data-stu-id="93650-289">If a JoinSymbol is returned, than its NameToExtent property contains a symbol for the needed property.</span></span> <span data-ttu-id="93650-290">Si le symbole de jointure représente une jointure imbriquée, une nouvelle paire de symboles est retournée avec le symbole de jointure pour suivre le symbole qui sera utilisé comme alias d'instance et le symbole qui représente la propriété réelle pour une résolution ultérieure.</span><span class="sxs-lookup"><span data-stu-id="93650-290">If the join symbol represents a nested join, a new Symbol pair is returned with the join symbol to track the symbol that would be used as the instance alias, and the symbol representing the actual property for further resolving.</span></span>

- <span data-ttu-id="93650-291">Si un SymbolPair est retourné et la partie de la colonne est un symbole de jointure, un symbole de jointure est encore retourné, mais dans ce cas la propriété de colonne est mise à jour pour pointer vers la propriété représentée par l'expression de propriété actuelle.</span><span class="sxs-lookup"><span data-stu-id="93650-291">If a SymbolPair is returned and the Column part is a join symbol, a join symbol is again returned, but now the column property is updated to point to the property represented by the current property expression.</span></span> <span data-ttu-id="93650-292">Dans le cas contraire, un SqlBuilder est retourné avec le SymbolPair source en tant qu'alias et le symbole de la propriété actuelle en tant que colonne.</span><span class="sxs-lookup"><span data-stu-id="93650-292">Otherwise a SqlBuilder is returned with the SymbolPair source as the alias, and the symbol for the current property as the column.</span></span>

- <span data-ttu-id="93650-293">Si un symbole est retourné, la méthode Visit retourne une méthode SqlBuilder avec cette instance en tant qu'alias et le nom de propriété en tant que nom de colonne.</span><span class="sxs-lookup"><span data-stu-id="93650-293">If a Symbol is returned, the Visit method returns a SqlBuilder method with that instance as the alias, and the property name as column name.</span></span>

### <a name="dbnewinstanceexpression"></a><span data-ttu-id="93650-294">DbNewInstanceExpression</span><span class="sxs-lookup"><span data-stu-id="93650-294">DbNewInstanceExpression</span></span>

<span data-ttu-id="93650-295">En cas d'utilisation comme propriété de projection de DbProjectExpression, DbNewInstanceExpression produit une liste séparée par des virgules des arguments afin de représenter les colonnes projetées.</span><span class="sxs-lookup"><span data-stu-id="93650-295">When used as the Projection property of DbProjectExpression, DbNewInstanceExpression produces a comma-separated list of the arguments to represent the projected columns.</span></span>

<span data-ttu-id="93650-296">Lorsque DbNewInstanceExpression possède un type de retour de collection et définit une nouvelle collection des expressions fournies en tant qu’arguments, les trois cas suivants sont gérés séparément :</span><span class="sxs-lookup"><span data-stu-id="93650-296">When DbNewInstanceExpression has a collection return type, and defines a new collection of the expressions provided as arguments, the following three cases are handled separately:</span></span>

- <span data-ttu-id="93650-297">Si DbNewInstanceExpression possède DbElementExpression en tant que seul argument, il est traduit comme suit :</span><span class="sxs-lookup"><span data-stu-id="93650-297">If DbNewInstanceExpression has DbElementExpression as the only argument, it is translated as follows:</span></span>

```sql
NewInstance(Element(X)) =>  SELECT TOP 1 …FROM X
```

<span data-ttu-id="93650-298">Si DbNewInstanceExpression n'a pas d'argument (représente une table vide), DbNewInstanceExpression est traduit par :</span><span class="sxs-lookup"><span data-stu-id="93650-298">If DbNewInstanceExpression has no arguments (represents an empty table), DbNewInstanceExpression is translated into:</span></span>

```sql
SELECT CAST(NULL AS <primitiveType>) as X
FROM (SELECT 1) AS Y WHERE 1=0
```

<span data-ttu-id="93650-299">Dans le cas contraire, DbNewInstanceExpression génère une échelle union-all des arguments :</span><span class="sxs-lookup"><span data-stu-id="93650-299">Otherwise DbNewInstanceExpression builds a union-all ladder of the arguments:</span></span>

```sql
SELECT <visit-result-arg1> as X
UNION ALL SELECT <visit-result-arg2> as X
UNION ALL …
UNION ALL SELECT <visit-result-argN> as X
```

### <a name="dbfunctionexpression"></a><span data-ttu-id="93650-300">DbFunctionExpression</span><span class="sxs-lookup"><span data-stu-id="93650-300">DbFunctionExpression</span></span>

<span data-ttu-id="93650-301">Les fonctions canoniques et intégrées sont traitées de la même façon : si elles nécessitent une gestion particulière (TRIM(string) à LTRIM(RTRIM(string), par exemple), le gestionnaire approprié est appelé.</span><span class="sxs-lookup"><span data-stu-id="93650-301">Canonical and built-in functions are processed the same way: if they need special handling (TRIM(string) to  LTRIM(RTRIM(string), for example), the appropriate handler is invoked.</span></span> <span data-ttu-id="93650-302">Dans le cas contraire, elles sont traduites en FunctionName(arg1, arg2, ..., argn).</span><span class="sxs-lookup"><span data-stu-id="93650-302">Otherwise they are translated to FunctionName(arg1, arg2, ..., argn).</span></span>

<span data-ttu-id="93650-303">Les dictionnaires sont utilisés pour effectuer le suivi des fonctions qui nécessitent une gestion particulière et de leurs gestionnaires appropriés.</span><span class="sxs-lookup"><span data-stu-id="93650-303">Dictionaries are used to keep track of which functions need special handling and their appropriate handlers.</span></span>

<span data-ttu-id="93650-304">Les fonctions définies par l’utilisateur sont traduites en NomEspaceNoms. nomfonction (Arg1, Arg2,..., argN).</span><span class="sxs-lookup"><span data-stu-id="93650-304">User-defined functions are translated to NamespaceName.FunctionName(arg1, arg2, ..., argn).</span></span>

### <a name="dbelementexpression"></a><span data-ttu-id="93650-305">DbElementExpression</span><span class="sxs-lookup"><span data-stu-id="93650-305">DbElementExpression</span></span>

<span data-ttu-id="93650-306">La méthode qui visite DbElementExpression est appelée uniquement pour visiter un DbElementExpression lorsqu'il est utilisé pour représenter une sous-requête scalaire.</span><span class="sxs-lookup"><span data-stu-id="93650-306">The method that visits DbElementExpression is only invoked for visiting a DbElementExpression when used to represent a scalar subquery.</span></span> <span data-ttu-id="93650-307">Par conséquent, DbElementExpression traduit par un SqlSelectStatement complet et le met entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="93650-307">Therefore, DbElementExpression translates into a complete SqlSelectStatement and adds brackets around it.</span></span>

### <a name="dbquantifierexpression"></a><span data-ttu-id="93650-308">DbQuantifierExpression</span><span class="sxs-lookup"><span data-stu-id="93650-308">DbQuantifierExpression</span></span>

<span data-ttu-id="93650-309">Selon le type d’expression (any ou All), DbQuantifierExpression est traduit comme suit :</span><span class="sxs-lookup"><span data-stu-id="93650-309">Depending on the expression type (Any or All), DbQuantifierExpression is translated as:</span></span>

```sql
Any(input, x) => Exists(Filter(input,x))
All(input, x) => Not Exists(Filter(input, not(x))
```

### <a name="dbnotexpression"></a><span data-ttu-id="93650-310">DbNotExpression</span><span class="sxs-lookup"><span data-stu-id="93650-310">DbNotExpression</span></span>

<span data-ttu-id="93650-311">Dans certains cas, il est possible de réduire la traduction de DbNotExpression par son expression d‘entrée.</span><span class="sxs-lookup"><span data-stu-id="93650-311">In some cases it is possible to collapse the translation of DbNotExpression with its input expression.</span></span> <span data-ttu-id="93650-312">Exemple :</span><span class="sxs-lookup"><span data-stu-id="93650-312">For example:</span></span>

```sql
Not(IsNull(a)) =>  "a IS NOT NULL"
Not(All(input, x) => Not (Not Exists(Filter(input, not(x))) => Exists(Filter(input, not(x))
```

<span data-ttu-id="93650-313">La raison pour laquelle la deuxième réduction est effectuée est que des inefficacités ont été introduites par le fournisseur lors de la traduction de DbQuantifierExpression de type All.</span><span class="sxs-lookup"><span data-stu-id="93650-313">The reason the second collapse is performed is because inefficiencies were introduced by the provider when translating DbQuantifierExpression of type All.</span></span> <span data-ttu-id="93650-314">Donc l'Entity Framework n'a pas pu faire la simplification.</span><span class="sxs-lookup"><span data-stu-id="93650-314">Thus the Entity Framework could not have done the simplification.</span></span>

### <a name="dbisemptyexpression"></a><span data-ttu-id="93650-315">DbIsEmptyExpression</span><span class="sxs-lookup"><span data-stu-id="93650-315">DbIsEmptyExpression</span></span>

<span data-ttu-id="93650-316">DbIsEmptyExpression est traduit par :</span><span class="sxs-lookup"><span data-stu-id="93650-316">DbIsEmptyExpression is translated as:</span></span>

```sql
IsEmpty(input) = Not Exists(input)
```

## <a name="second-phase-of-sql-generation-generating-the-string-command"></a><span data-ttu-id="93650-317">Deuxième phase de la génération SQL : génération de la commande de chaîne</span><span class="sxs-lookup"><span data-stu-id="93650-317">Second Phase of SQL Generation: Generating the String Command</span></span>

<span data-ttu-id="93650-318">Lors de la génération d'une commande SQL de chaîne, le SqlSelectStatement produit des alias réels pour les symboles, ce qui résout le problème du changement de nom de colonne et d'alias de l'étendue.</span><span class="sxs-lookup"><span data-stu-id="93650-318">When generating a string SQL command, the SqlSelectStatement produces actual aliases for the symbols, which addresses the issue of column name and extent alias renaming.</span></span>

<span data-ttu-id="93650-319">Le changement de nom de l'alias de l'étendue se produit lors de l'écriture de l'objet SqlSelectStatement dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="93650-319">Extent alias renaming occurs while writing the SqlSelectStatement object into a string.</span></span> <span data-ttu-id="93650-320">En premier lieu créez une liste de tous les alias utilisés par les étendues externes.</span><span class="sxs-lookup"><span data-stu-id="93650-320">First create a list of all the aliases used by the outer extents.</span></span> <span data-ttu-id="93650-321">Chaque symbole du FromExtents (ou AllJoinExtents si la valeur n'est pas null), est renommé s'il entre en conflit avec l'une des étendues externes.</span><span class="sxs-lookup"><span data-stu-id="93650-321">Each symbol in the FromExtents (or AllJoinExtents if it is non-null), gets renamed if it collides with any of the outer extents.</span></span> <span data-ttu-id="93650-322">Si le changement de nom est exigé, il n'entrera en conflit avec aucune des étendues collectées dans AllExtentNames.</span><span class="sxs-lookup"><span data-stu-id="93650-322">If renaming is needed, it will not conflict with any of the extents collected in AllExtentNames.</span></span>

<span data-ttu-id="93650-323">Le changement de nom des colonnes se produit lors de l'écriture d'un objet Symbol dans une chaîne.</span><span class="sxs-lookup"><span data-stu-id="93650-323">Column renaming occurs while writing a Symbol object to a string.</span></span> <span data-ttu-id="93650-324">AddDefaultColumns dans la première phase a déterminé si un certain symbole de colonne doit être renommé.</span><span class="sxs-lookup"><span data-stu-id="93650-324">AddDefaultColumns in the first phase has determined if a certain column symbol has to be renamed.</span></span> <span data-ttu-id="93650-325">Dans la deuxième phase le changement de nom se produit en s'assurant que le nom généré n'entre en conflit avec aucun des noms utilisés dans AllColumnNames</span><span class="sxs-lookup"><span data-stu-id="93650-325">In the second phase only the rename occurs making sure that the name produced does not conflict with any name used in AllColumnNames</span></span>

<span data-ttu-id="93650-326">Pour produire des noms uniques pour les alias d’étendue et pour les colonnes, utilisez \<existing_name > _n, où n est le plus petit alias qui n’a pas encore été utilisé.</span><span class="sxs-lookup"><span data-stu-id="93650-326">To produce unique names both for extent aliases and for columns, use \<existing_name>_n where n is the smallest alias that has not been used yet.</span></span> <span data-ttu-id="93650-327">La liste globale de tous les alias augmente le besoin d'un changement de nom en cascade.</span><span class="sxs-lookup"><span data-stu-id="93650-327">The global list of all aliases increases the need for cascading renames.</span></span>

## <a name="see-also"></a><span data-ttu-id="93650-328">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="93650-328">See also</span></span>

- [<span data-ttu-id="93650-329">Génération SQL dans l’exemple de fournisseur</span><span class="sxs-lookup"><span data-stu-id="93650-329">SQL Generation in the Sample Provider</span></span>](sql-generation-in-the-sample-provider.md)
