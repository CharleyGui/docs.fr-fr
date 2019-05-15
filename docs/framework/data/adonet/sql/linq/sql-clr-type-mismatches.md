---
title: Incompatibilité entre types SQL-CLR
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0a90c33f-7ed7-4501-ad5f-6224c5da8e9b
ms.openlocfilehash: e51d999d5fcaf8180b4ea5189a3db9b6143a57db
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65582721"
---
# <a name="sql-clr-type-mismatches"></a>Incompatibilité entre types SQL-CLR

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] automatise en grande partie la traduction entre le modèle objet et SQL Server. Certaines situations ne permettent toutefois pas une traduction exacte. Cette incompatibilité majeure entre les types CLR (Common Language Runtime) et les types de base de données SQL Server est résumée dans les sections suivantes. Vous trouverez plus d’informations sur les mappages de types spécifiques et de traduction de fonctions à [le mappage de Type SQL-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md) et [Types de données et fonctions](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md).

## <a name="data-types"></a>Types de données

La traduction entre CLR et SQL Server se produit lorsqu'une requête est envoyée à la base de données, et lorsque les résultats sont renvoyés au modèle objet. Par exemple, la requête Transact-SQL suivante requiert deux conversions de valeurs :

```sql
Select DateOfBirth From Customer Where CustomerId = @id
```

Pour que la requête soit exécutée sur SQL Server, vous devez spécifier la valeur du paramètre Transact-SQL. Dans cet exemple, la valeur du paramètre `id` doit d'abord être traduite d'un type <xref:System.Int32?displayProperty=nameWithType> CLR en un type `INT` SQL Server afin que la base de données puisse comprendre en quoi consiste cette valeur. Puis pour récupérer les résultats, la colonne `DateOfBirth` SQL Server doit être traduite d'un type `DATETIME` SQL Server en un type <xref:System.DateTime?displayProperty=nameWithType> CLR à des fins d'utilisation dans le modèle objet. Dans cet exemple, les types du modèle objet CLR et de la base de données SQL Server ont des mappages naturels. Mais ce n'est pas toujours le cas.

### <a name="missing-counterparts"></a>Équivalents manquants

Les types suivants n'ont pas d'équivalents raisonnables.

- Incompatibilités dans l'espace de noms <xref:System> CLR :

  - **Entiers non signés**. Ces types sont généralement mappés à leurs équivalents signés de plus grande taille pour éviter le dépassement de capacité. Les littéraux peuvent être convertis en numérique signé de taille équivalente ou inférieure, selon la valeur.

  - **Booléenne**. Ces types peuvent être mappés à un bit ou à un numérique ou une chaîne de taille supérieure. Un littéral peut être mappé à une expression qui correspond à la même valeur (par exemple, `1=1` dans SQL pour `True` dans CLS).

  - **TimeSpan**. Ce type représente la différence entre deux valeurs `DateTime` et ne correspond pas au `timestamp` de SQL Server. Dans certains cas, le <xref:System.TimeSpan?displayProperty=nameWithType> CLR peut également mapper au type `TIME` SQL Server. Le type `TIME` SQL Server a pour but de représenter les valeurs positives inférieures à 24 heures. Le <xref:System.TimeSpan> CLR offre une plage beaucoup plus étendue.

  > [!NOTE]
  > Les types .NET Framework pour SQL Server spécifique dans <xref:System.Data.SqlTypes> ne sont pas inclus dans cette comparaison.

- Incompatibilités dans SQL Server :

  - **Types de caractères de longueur fixe**. Transact-SQL fait la distinction entre les catégories Unicode et non Unicode et possède trois types distincts dans chaque catégorie : longueur fixe `nchar` / `char`, longueur variable `nvarchar` / `varchar`, et plus grande taille `ntext` / `text`. Les types de caractères de longueur fixe peuvent être mappés au type <xref:System.Char?displayProperty=nameWithType> CLR pour récupérer des caractères, mais ils ne correspondent pas vraiment au même type dans les conversions et le comportement.

  - **Bit**. Bien que le domaine `bit` présente le même nombre de valeurs que `Nullable<Boolean>`, il s'agit de deux types différents. `Bit` prend les valeurs `1` et `0` au lieu de `true` / `false`et ne peut pas être utilisé comme un équivalent aux expressions booléennes.

  - **Horodatage**. Contrairement au type <xref:System.TimeSpan?displayProperty=nameWithType> CLR, le type `TIMESTAMP` SQL Server représente un nombre de 8 octets généré par la base de données qui est unique pour chaque mise à jour et n'est pas basé sur la différence entre des valeurs <xref:System.DateTime>.

  - **Money** et **SmallMoney**. Ces types peuvent être mappés à <xref:System.Decimal> mais ils sont fondamentalement différents et sont traités comme tels par les fonctions et les conversions serveur.

### <a name="multiple-mappings"></a>Mappages multiples

Il existe également de nombreux types de données SQL Server que vous pouvez mapper à un ou plusieurs types de données CLR. Il existe également de nombreux types CLR que vous pouvez mapper à un ou plusieurs types SQL Server. Même si un mappage est pris en charge par LINQ to SQL, cela n'implique pas nécessairement que deux types mappés entre CLR et SQL Server présenteront une précision, une plage et une sémantique identiques. Certains mappages peuvent inclure des différences au niveau de tout ou partie de ces trois aspects. Vous trouverez plus d’informations sur ces différences éventuelles pour les diverses possibilités de mappage au [mappage de Type SQL-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).

### <a name="user-defined-types"></a>Types définis par l'utilisateur

Les types CLR définis par l'utilisateur sont conçus pour aider à combler le fossé entre les systèmes de types. Ils présentent néanmoins des problèmes intéressants concernant le versioning de type. Une modification de la version du client peut ne pas avoir de modification correspondante dans le type stocké sur le serveur de base de données. Toute modification de ce type entraîne une autre incompatibilité de type où la sémantique de type risque de ne pas correspondre et la différence de version peut devenir visible. D'autres complications interviennent puisque les hiérarchies d'héritage sont refactorisées dans les versions successives.

## <a name="expression-semantics"></a>Sémantique d'expression

Outre l'incompatibilité par paire entre les types CLR et de base de données, les expressions compliquent l'incompatibilité. Les incompatibilités dans la sémantique d'opérateur, la sémantique de fonction, la conversion de type implicite et les règles de priorité doivent être prises en compte.

Les sous-sections suivantes illustrent l'incompatibilité entre des expressions apparemment similaires. Il est possible de générer des expressions SQL qui sont sémantiquement équivalentes à une expression CLR donnée. Toutefois, on ne peut pas déterminer avec précision si les différences sémantiques entre des expressions apparemment similaires sont évidentes pour un utilisateur CLR, et par conséquent si les modifications requises pour l'équivalence sémantique sont prévues ou non. Un problème particulièrement critique se pose lors de l'évaluation d'une expression pour un ensemble de valeurs. La visibilité de la différence peut dépendre des données et être difficile à identifier pendant le codage et le débogage.

### <a name="null-semantics"></a>Sémantique Null

Les expressions SQL fournissent la logique à trois valeurs pour les expressions booléennes. Le résultat peut être true, false ou null. CLR spécifie un résultat booléen à deux valeurs pour les comparaisons impliquant des valeurs null. Examinons le code ci-dessous.

[!code-csharp[DLinqMismatch#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#2)]
[!code-vb[DLinqMismatch#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#2)]

```sql
-- Assume col1 and col2 are integer columns with null values.
-- Assume that ANSI null behavior has not been explicitly
--  turned off.
Select …
From …
Where col1 = col2
-- Evaluates to null, not true and the corresponding row is not
--   selected.
-- To obtain matching behavior (i -> col1, j -> col2) change
--   the query to the following:
Select …
From …
Where
    col1 = col2
or (col1 is null and col2 is null)
-- (Visual Basic 'Nothing'.)
```

Un problème similaire se produit avec l'hypothèse concernant les résultats à deux valeurs.

[!code-csharp[DLinqMismatch#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#3)]
[!code-vb[DLinqMismatch#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#3)]

```sql
-- Assume col1 and col2 are nullable columns.
-- Assume that ANSI null behavior has not been explicitly
--   turned off.
Select …
From …
Where
    col1 = col2
or col1 != col2
-- Visual Basic: col1 <> col2.

-- Excludes the case where the boolean expression evaluates
--   to null. Therefore the where clause does not always
--   evaluate to true.
```

Dans le cas précédent, vous pouvez obtenir un comportement équivalent en générant du SQL, mais la traduction risque de ne pas refléter correctement votre intention.

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] n’impose pas C# `null` ou Visual Basic `nothing` sémantique de comparaison sur SQL. Les opérateurs de comparaison sont traduits syntaxiquement dans leurs équivalents SQL. La sémantique reflète la sémantique SQL définie par les paramètres du serveur ou de la connexion. Deux valeurs null sont considérées comme différentes selon les paramètres SQL Server (bien que vous puissiez modifier les paramètres pour changer la sémantique). Quoi qu'il en soit, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ne tient pas compte des paramètres du serveur lors de la traduction de requête.

Une comparaison avec le littéral `null` (`nothing`) est traduite dans la version SQL appropriée (`is null` ou `is not null`).

La valeur `null` (`nothing`) dans le classement est définie par SQL Server et [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ne change pas le classement.

### <a name="type-conversion-and-promotion"></a>Conversion et promotion de type

SQL prend en charge un ensemble complet de conversions implicites d'expressions. Des expressions similaires en C# nécessiteraient un cast explicite. Exemple :

- Les types `Nvarchar` et `DateTime` peuvent être comparés dans SQL sans cast explicite mais C# nécessite une conversion explicite.

- `Decimal` est converti implicitement en `DateTime` dans SQL. C# n'autorise pas de conversion implicite.

De même, la priorité des types de Transact-SQL diffère de celle de C# car l'ensemble de types sous-jacent est différent. En fait, il n'existe pas de relation sous-ensemble/sur-ensemble claire entre les listes de priorités. Par exemple, la comparaison d'un `nvarchar` avec un `varchar` entraîne la conversion implicite de l'expression `varchar` en `nvarchar`. CLR ne fournit aucune promotion équivalente.

Dans les cas simples, ces différences soumettent les expressions CLR à des casts redondants pour une expression SQL correspondante. Plus important, les résultats intermédiaires d'une expression SQL risquent de faire l'objet d'une promotion implicite en un type qui ne présente aucun équivalent exact en C# et inversement. De manière générale, le test, le débogage et la validation de ce type d'expressions représentent une charge de travail supplémentaire pour l'utilisateur.

### <a name="collation"></a>Classement

Transact-SQL prend en charge des classements explicites tels que les annotations des types de chaînes de caractères. Ces classements déterminent la validité de certaines comparaisons. Par exemple, la comparaison de deux colonnes avec des classements explicites différents est une erreur. L'utilisation d'un type de chaîne CTS très simplifié ne provoque pas de telles erreurs. Prenons l'exemple suivant :

```sql
create table T2 (
    Col1 nvarchar(10),
    Col2      nvarchar(10) collate Latin_general_ci_as
)
```

[!code-csharp[DLinqMismatch#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#4)]
[!code-vb[DLinqMismatch#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#4)]

```sql
Select …
From …
Where Col1 = Col2
-- Error, collation conflict.
```

En effet, la sous-clause de classement crée un *restreint type* qui n’est pas substituable.

De même, l'ordre de tri peut être considérablement différent selon les systèmes de type. Cette différence concerne le tri des résultats. <xref:System.Guid> est trié sur les 16 octets dans l'ordre lexicographique (`IComparable()`), tandis que T-SQL compare les GUID dans l'ordre suivant : node(10-15), clock-seq(8-9), time-high(6-7), time-mid(4-5), time-low(0-3). Cette organisation a été définie dans SQL 7.0 lorsque les GUID générés par NT présentaient cet ordre d'octets. Cette approche a permis de s'assurer que les GUID générés sur le même cluster de nœuds se présentaient dans l'ordre séquentiel en fonction de l'horodatage. Elle s'est également avérée utile pour la génération d'index (les insertions deviennent des ajouts plutôt que des E/S aléatoires). L'ordre a été brouillé ultérieurement dans Windows en raison de problèmes de confidentialité, mais SQL doit maintenir la compatibilité. Une solution de contournement consiste à utiliser <xref:System.Data.SqlTypes.SqlGuid> au lieu de <xref:System.Guid>.

### <a name="operator-and-function-differences"></a>Différences d'opérateur et de fonction

Les opérateurs et les fonctions qui sont pour l'essentiel comparables ont une sémantique légèrement différente. Exemple :

- C# spécifie une sémantique de « court-circuit » selon l’ordre lexical des opérandes pour les opérateurs logiques `&&` et `||`. SQL est destiné aux requêtes basées sur des ensembles et laisse par conséquent une plus grande marge de manœuvre à l'optimiseur pour décider de l'ordre d'exécution. Les conséquences sont notamment les suivantes :

  - Traduction sémantiquement équivalente nécessiterait «`CASE` ... `WHEN` … `THEN`« construire dans SQL pour éviter la réorganisation d’exécution des opérandes.

  - Une traduction faible dans `AND` / `OR` opérateurs peuvent entraîner des erreurs inattendues si les C# expression repose sur l’évaluation de la deuxième opérande basée sur le résultat de l’évaluation du premier opérande.

- `Round()` fonction a une sémantique différente dans .NET Framework et dans T-SQL.

- L'index de départ des chaînes correspond à 0 dans CLR et à 1 dans SQL. Par conséquent, toute fonction comportant des index nécessite une traduction des index.

- Contrairement à SQL, CLR prend en charge l'opérateur modulo (%) pour les nombres à virgule flottante.

- L'opérateur `Like` acquiert efficacement des surcharges automatiques selon des conversions implicites. Bien que l'opérateur `Like` soit défini pour fonctionner sur des types de chaînes de caractères, la conversion implicite de types numériques ou types `DateTime` permet également l'utilisation de ces types non-chaînes avec `Like`. Dans CTS, il n'existe pas de conversion implicite comparable. Par conséquent, des surcharges supplémentaires sont nécessaires.

    > [!NOTE]
    > Ce comportement de l'opérateur `Like` s'applique uniquement à C# ; le mot clé `Like` de Visual Basic reste inchangé.

- Dépassement de capacité est toujours vérifié dans SQL, mais il doit être spécifié explicitement dans C# (pas dans Visual Basic) pour éviter le bouclage. Considérons des colonnes d'entiers C1, C2 et C3, si C1+C2 est stocké dans C3 (Update T Set C3 = C1+C2).

    ```sql
    create table T3 (
        Col1      integer,
        Col2      integer
    )
    insert into T3 (col1, col2) values (2147483647, 5)
    -- Valid values: max integer value and 5.
    select * from T3 where col1 + col2 < 0
    -- Produces arithmetic overflow error.
    ```

[!code-csharp[DLinqMismatch#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#5)]
[!code-vb[DLinqMismatch#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#5)]

- SQL effectue un arrondi arithmétique symétrique tandis que .NET Framework utilise l’arrondi bancaire. Pour plus d'informations, consultez l'article 196652 de la Base de connaissances.

- Par défaut, les comparaisons de chaînes de caractères ne sont pas sensibles à la casse dans SQL pour les paramètres régionaux communs. Dans Visual Basic et C#, elles sont sensibles à la casse. Par exemple, `s == "Food"` (`s = "Food"` en Visual Basic) et `s == "Food"` peuvent donner des résultats différents si `s` est `food`.

    ```sql
    -- Assume default US-English locale (case insensitive).
    create table T4 (
        Col1      nvarchar (256)
    )
    insert into T4 values (‘Food’)
    insert into T4 values (‘FOOD’)
    select * from T4 where Col1 = ‘food’
    -- Both the rows are returned because of case-insensitive matching.
    ```

[!code-csharp[DLinqMismatch#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#6)]
[!code-vb[DLinqMismatch#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#6)]

- Les opérateurs/fonctions appliqués aux arguments de type de caractères de longueur fixe dans SQL ont une sémantique sensiblement différente par rapport aux mêmes opérateurs/fonctions appliqués à un objet <xref:System.String?displayProperty=nameWithType> CLR. Cela peut également être considéré comme une extension du problème d’équivalents manquants abordé dans la section consacrée aux types.

    ```sql
    create table T4 (
        Col1      nchar(4)
    )
    Insert into T5(Col1) values ('21');
    Insert into T5(Col1) values ('1021');
    Select * from T5 where Col1 like '%1'
    -- Only the second row with Col1 = '1021' is returned.
    -- Not the first row!
    ```

     [!code-csharp[DLinqMismatch#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#7)]
     [!code-vb[DLinqMismatch#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#7)]

     La concaténation de chaînes pose le même problème.

    ```sql
    create table T6 (
        Col1      nchar(4)
        Col2       nchar(4)
    )
    Insert into T6 values ('a', 'b');
    Select Col1+Col2 from T6
    -- Returns concatenation of padded strings "a   b   " and not "ab".
    ```

En résumé, une traduction circonvolutionnée peut être requise pour les expressions CLR et des opérateurs/fonctions supplémentaires peuvent être nécessaires pour exposer les fonctionnalités SQL.

### <a name="type-casting"></a>Cast de type

Dans C# et SQL, les utilisateurs peuvent substituer la sémantique par défaut d'expressions en utilisant des casts de types explicites (`Cast` et `Convert`). Toutefois, l'exposition de cette fonction sur la limite du système de type crée un dilemme. Un cast SQL qui fournit la sémantique souhaitée ne peut pas être traduit facilement en cast C# correspondant. Par contre, un cast C# ne peut pas être traduit directement en cast SQL équivalent en raison des incompatibilités de type, des équivalents manquants et des hiérarchies de priorité des types. Il existe un compromis entre l'exposition de l'incompatibilité du système de type et une perte importante de puissance d'expression.

Dans d’autres cas, le cast de type peut ne pas être nécessaire dans un domaine de validation d’une expression mais peut être requis pour s’assurer qu’un mappage non défini par défaut est appliqué correctement à l’expression.

```sql
-- Example from "Non-default Mapping" section extended
create table T5 (
    Col1      nvarchar(10),
    Col2      nvarchar(10)
)
Insert into T5(col1, col2) values (‘3’, ‘2’);
```

[!code-csharp[DLinqMismatch#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#8)]
[!code-vb[DLinqMismatch#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#8)]

```sql
Select *
From T5
Where Col1 + Col2 > 4
-- "Col1 + Col2" expr evaluates to '32'
```

## <a name="performance-issues"></a>Problèmes de performances

Gestion des comptes pour certains CLR SQL Server-différences de type peuvent entraîner une baisse des performances lors du passage entre le CLR et SQL Server des systèmes de type. Voici quelques exemples de scénarios affectant les performances :

- Ordre d'évaluation de la logique et/ou des opérateurs forcé

- La génération de SQL pour appliquer l'ordre d'évaluation des prédicats limite les capacités de l'optimiseur SQL.

- Les conversions de type, qu'elles soient introduites par un compilateur CLR ou par une implémentation de requête objet-relationnel, peuvent réduire l'utilisation de l'index.

     Par exemple :

    ```sql
    -- Table DDL
    create table T5 (
        Col1      varchar(100)
    )
    ```

     [!code-csharp[DLinqMismatch#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqMismatch/cs/Program.cs#9)]
     [!code-vb[DLinqMismatch#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqMismatch/vb/Module1.vb#9)]

     Prenons la traduction de l'expression `(s = SOME_STRING_CONSTANT)`.

    ```sql
    -- Corresponding part of SQL where clause
    Where …
    Col1 = SOME_STRING_CONSTANT
    -- This expression is of the form <varchar> = <nvarchar>.
    -- Hence SQL introduces a conversion from varchar to nvarchar,
    --   resulting in
    Where …
    Convert(nvarchar(100), Col1) = SOME_STRING_CONSTANT
    -- Cannot use the index for column Col1 for some implementations.
    ```

Outre les différences sémantiques, il est important de prendre en compte l'impact sur les performances lors du passage entre les systèmes de types SQL Server et CLR. Pour les grands groupes de données, de tels problèmes de performances peuvent déterminer si une application est déployable.

## <a name="see-also"></a>Voir aussi

- [Informations générales](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
