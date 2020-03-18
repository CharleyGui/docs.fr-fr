---
title: Indépendance du langage et composants indépendants du langage
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- language interoperability
- Common Language Specification
- cross-language interoperability
- CLS
- runtime, language interoperability
- common language runtime, language interoperability
ms.assetid: 4f0b77d0-4844-464f-af73-6e06bedeafc6
ms.openlocfilehash: 689ca9f7278dcf91b12bc62b5255a968388bb9f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400532"
---
# <a name="language-independence-and-language-independent-components"></a>Indépendance du langage et composants indépendants du langage

Le .NET Framework est indépendant du langage. Cela signifie qu'en tant que développeur, vous pouvez développer dans l'un des nombreux langages qui ciblent le .NET Framework, tels que C#, C++/CLI, Eiffel, F#, IronPython, IronRuby, PowerBuilder, Visual Basic, Visual COBOL et Windows PowerShell. Vous pouvez accéder aux types et aux membres des bibliothèques de classes développées pour le .NET Framework sans avoir à connaître le langage dans lequel ils ont été initialement écrits ni à suivre les conventions du langage d'origine. Si vous développez des composants, votre composant est accessible par toute application .NET Framework, indépendamment de son langage.

> [!NOTE]
> La première partie de cet article décrit la création de composants indépendants du langage, c'est-à-dire de composants qui peuvent être utilisés par des applications écrites dans n'importe quel langage. Vous pouvez également créer un composant ou une application unique à partir de code source écrit dans plusieurs langages. Consultez [Interopérabilité multilingue](#CrossLang) dans la deuxième partie de cet article.

Pour interagir entièrement avec d’autres objets écrits dans un langage quelconque, les objets ne doivent exposer aux appelants que les fonctionnalités communes à tous les langages. Cet ensemble commun de fonctionnalités est défini par la spécification CLS (Common Language Specification), qui est un ensemble de règles qui s’appliquent aux assemblys générés. La spécification CLS (Common Language Specification) est définie dans la Partition I, clauses 7 à 11 du document [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

Si votre composant est conforme à la spécification CLS, il est garanti d'être conforme CLS et accessible à partir du code dans les assemblys écrits dans n'importe quel langage de programmation qui prend en charge la spécification CLS. Vous pouvez déterminer si votre composant est conforme à la spécification CLS (Common Language Specification) au moment de la compilation en appliquant l'attribut <xref:System.CLSCompliantAttribute> à votre code source. Pour plus d’informations, consultez [Attribut CLSCompliantAttribute](#CLSAttribute).

Contenu de cet article :

- [Règles de conformité CLS](#Rules)

  - [Types et signatures de membres de types](#Types)

  - [Conventions de nommage](#naming)

  - [Conversion de type](#conversion)

  - [Tableaux](#arrays)

  - [Interfaces](#Interfaces)

  - [Énumérations](#enums)

  - [Membres de types en général](#members)

  - [Accessibilité des membres](#MemberAccess)

  - [Types et membres génériques](#Generics)

  - [Constructeurs](#ctors)

  - [Propriétés](#properties)

  - [Événements](#events)

  - [Overloads](#overloads)

  - [Exceptions](#exceptions)

  - [Attributs](#attributes)

- [Attribut CLSCompliantAttribute](#CLSAttribute)

- [Interopérabilité interlangage](#CrossLang)

<a name="Rules"></a>

## <a name="cls-compliance-rules"></a>Règles de conformité CLS

Cette section présente les règles de création d'un composant conforme à CLS. Pour obtenir une liste complète des règles, consultez la Partition I, clause 11 du document [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm).

> [!NOTE]
> La spécification CLS (Common Language Specification) présente chaque règle de conformité CLS telle qu'elle s'applique aux consommateurs (les développeurs qui accèdent par programme à un composant conforme CLS), aux infrastructures (les développeurs qui utilisent un compilateur de langage pour créer des bibliothèques conformes CLS) et aux extendeurs (les développeurs qui créent un outil tel qu'un compilateur de langage ou un analyseur de code qui crée des composants conformes CLS). Cet article se concentre sur les règles applicables aux infrastructures. Notez, toutefois, qu'une partie des règles qui s'appliquent aux extendeurs peut également s'appliquer aux assemblys créés à l'aide de Reflection.Emit.

Pour concevoir un composant indépendant du langage, vous n'avez qu'à appliquer les règles de conformité CLS à l'interface publique de votre composant. Votre implémentation privée n'a pas besoin d'être conforme à la spécification.

> [!IMPORTANT]
> Les règles de conformité CLS s'appliquent uniquement à l'interface publique d'un composant, pas à son implémentation privée.

Par exemple, les entiers non signés autres que <xref:System.Byte> ne sont pas conformes à CLS. Étant donné que la classe `Person` de l'exemple suivant expose une propriété `Age` de type <xref:System.UInt16>, le code suivant affiche un avertissement du compilateur.

[!code-csharp[Conceptual.CLSCompliant#1](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public1.cs#1)]
[!code-vb[Conceptual.CLSCompliant#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public1.vb#1)]

Vous pouvez rendre la classe `Person` conforme à CLS en remplaçant le type `Age` de la propriété <xref:System.UInt16> par <xref:System.Int16>, qui est un entier signé 16 bits conforme à CLS. Il n'est pas nécessaire de modifier le type du champ privé `personAge`.

[!code-csharp[Conceptual.CLSCompliant#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/public2.cs#2)]
[!code-vb[Conceptual.CLSCompliant#2](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/public2.vb#2)]

L'interface publique d'une bibliothèque inclut les éléments suivants :

- Définitions des classes publiques.

- Définitions des membres publics des classes publiques et définitions des membres accessibles aux classes dérivées (à savoir, membres protégés).

- Paramètres et types de retour des méthodes publiques des classes publiques, et paramètres et types de retour des méthodes accessibles aux classes dérivées.

Les règles de conformité CLS sont répertoriées dans le tableau suivant. Le texte des règles est repris mot pour mot du document [ECMA-335 Standard: Common Language Infrastructure](https://www.ecma-international.org/publications/standards/Ecma-335.htm), qui est protégé par copyright 2012 par Ecma International. Vous trouverez des informations plus détaillées sur ces règles dans les sections suivantes.

|Category|Consultez|Règle|Numéro de règle|
|--------------|---------|----------|-----------------|
|Accessibilité|[Accessibilité des membres](#MemberAccess)|L'accessibilité ne devra pas être changée lors du remplacement de méthodes héritées, sauf en cas de remplacement d'une méthode héritée d'un assembly différent avec accessibilité `family-or-assembly`. Dans ce cas, le remplacement devra posséder l'accessibilité `family`.|10|
|Accessibilité|[Accessibilité des membres](#MemberAccess)|La visibilité et l'accessibilité des types et des membres seront déterminées de telle sorte que les types utilisés dans la signature d'un membre seront visibles et accessibles lorsque le membre proprement dit est visible et accessible. Par exemple, une méthode publique qui est visible à l'extérieur de son assembly n'aura pas d'argument dont le type est visible uniquement dans l'assembly. La visibilité et l'accessibilité des types composant un type générique instancié utilisé dans la signature d'un membre seront visibles et accessibles lorsque le membre proprement dit est visible et accessible. Par exemple, un type générique instancié présent dans la signature d'un membre qui est visible à l'extérieur de l'assembly n'aura pas d'argument générique dont le type est visible uniquement dans l'assembly.|12|
|Tableaux|[Tableaux](#arrays)|Les tableaux auront des éléments avec un type conforme à CLS, et toutes les dimensions du tableau auront des limites inférieures égales à zéro. Seul le fait qu'un élément soit un tableau et le type d'élément du tableau seront requis pour distinguer les surcharges. Lorsque la surcharge est basée sur deux ou plusieurs types de tableau, les types d'élément seront des types nommés.|16|
|Attributs|[Attributs](#attributes)|Les attributs seront de type <xref:System.Attribute?displayProperty=nameWithType> ou d'un type qui hérite de celui-ci.|41|
|Attributs|[Attributs](#attributes)|La spécification CLS autorise uniquement un sous-ensemble des encodages d'attributs personnalisés. Les seuls types autorisés à figurer dans ces encodages seront (voir Partition IV) : <xref:System.Type?displayProperty=nameWithType>, <xref:System.String?displayProperty=nameWithType>, <xref:System.Char?displayProperty=nameWithType>, <xref:System.Boolean?displayProperty=nameWithType>, <xref:System.Byte?displayProperty=nameWithType>, <xref:System.Int16?displayProperty=nameWithType>, <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Int64?displayProperty=nameWithType>, <xref:System.Single?displayProperty=nameWithType>, <xref:System.Double?displayProperty=nameWithType> et tout type d'énumération reposant sur un type entier de base conforme à CLS.|34|
|Attributs|[Attributs](#attributes)|La spécification CLS n'autorise pas les modificateurs obligatoires visibles publiquement (`modreq`, voir Partition II), mais autorise les modificateurs facultatifs (`modopt`, voir Partition II) qu'elle ne comprend pas.|35|
|Constructeurs|[Constructeurs](#ctors)|Un constructeur d'objet appellera un constructeur d'instance de sa classe de base avant tout accès aux données d'instance héritées. (Cela ne s'applique pas aux types de valeurs, qui n'ont pas besoin de constructeurs.)|21|
|Constructeurs|[Constructeurs](#ctors)|Un constructeur d'objet ne sera pas appelé sauf dans le cadre de la création d'un objet, et un objet ne sera pas initialisé deux fois.|22|
|Énumérations|[Énumérations](#enums)|Le type sous-jacent d'une énumération devra être un type d'entier CLS intégré, le nom du champ devra être « valeur__ » et ce champ devra être marqué `RTSpecialName`.|7|
|Énumérations|[Énumérations](#enums)|Il existe deux types distincts d'énumérations, signalés par la présence ou l'absence de l'attribut personnalisé <xref:System.FlagsAttribute?displayProperty=nameWithType> (voir Partition IV, Profiles and Libraries). L'un représente des valeurs entières nommées ; l'autre représente les indicateurs binaires nommés qui peuvent être combinés pour générer une valeur sans nom. La valeur d'une `enum` n'est pas limitée aux valeurs spécifiées.|8|
|Énumérations|[Énumérations](#enums)|Les champs static littéraux d’une énumération auront le type de l’énumération elle-même.|9|
|Événements|[Événements](#events)|Les méthodes qui implémentent un événement doivent être marquées `SpecialName` dans les métadonnées.|29|
|Événements|[Événements](#events)|L’accessibilité d’un événement et de ses accesseurs sera identique.|30|
|Événements|[Événements](#events)|Les méthodes `add` et `remove` d'un événement devront toutes les deux être présentes ou absentes.|31|
|Événements|[Événements](#events)|Les méthodes `add` et `remove` d'un événement devront chacune accepter un paramètre dont le type définit le type de l'événement et qui sera dérivé de <xref:System.Delegate?displayProperty=nameWithType>.|32|
|Événements|[Événements](#events)|Les événements adhéreront à un modèle d’attribution de nom spécifique. L'attribut `SpecialName` dont il est question dans la règle 29 de la spécification CLS sera ignoré dans les comparaisons de noms appropriées et respectera les règles d'identificateur.|33|
|Exceptions|[Exceptions](#exceptions)|Les objets levés seront de type <xref:System.Exception?displayProperty=nameWithType> ou d'un type qui hérite de celui-ci. Néanmoins, les méthodes conformes à CLS ne sont pas requises pour bloquer la propagation d'autres types d'exceptions.|40|
|Général|[Conformité CLS : les règles](#Rules)|Les règles CLS s'appliquent uniquement aux éléments d'un type qui sont accessibles ou visibles en dehors de l'assembly de définition.|1|
|Général|[Conformité CLS : les règles](#Rules)|Les membres de types non conformes à CLS ne seront pas marqués comme conformes à CLS.|2|
|Génériques|[Types et membres génériques](#Generics)|Les types imbriqués devront posséder au moins autant de paramètres génériques que le type englobant. Les paramètres génériques d'un type imbriqué ont la même position que les paramètres génériques du type englobant correspondant.|42|
|Génériques|[Types et membres génériques](#Generics)|Le nom d’un type générique devra encoder le nombre de paramètres de type déclarés sur le type non imbriqué ou récemment introduits dans le type s’il est imbriqué, selon les règles définies ci-dessus.|43|
|Génériques|[Types et membres génériques](#Generics)|Un type générique devra redéclarer les contraintes suffisantes afin de garantir que les contraintes sur le type de base ou les interfaces seraient satisfaites par les contraintes de type générique.|4444|
|Génériques|[Types et membres génériques](#Generics)|Les types utilisés comme contraintes sur les paramètres génériques devront eux-mêmes être conformes à CLS.|45|
|Génériques|[Types et membres génériques](#Generics)|La visibilité et l'accessibilité des membres (y compris des types imbriqués) d'un type générique instancié devront être définies dans l'instanciation spécifique plutôt que dans la déclaration générale du type générique. Sachant cela, les règles de visibilité et d'accessibilité de la règle 12 de la spécification CLS s'appliquent toujours.|46|
|Génériques|[Types et membres génériques](#Generics)|À chaque méthode générique abstraite ou virtuelle doit correspondre une implémentation concrète (non abstraite) par défaut.|47|
|Interfaces|[Interfaces](#Interfaces)|Les interfaces conformes à CLS ne devront pas nécessiter la définition de méthodes non conformes à CLS pour pouvoir les implémenter.|18|
|Interfaces|[Interfaces](#Interfaces)|Les interfaces conformes à CLS ne devront pas définir de méthodes statiques ni de champs.|19|
|Membres|[Membres de types en général](#members)|Les méthodes et les champs static globaux ne sont pas conformes CLS.|36|
|Membres|--|La valeur d'un champ statique littéral est spécifiée via l'utilisation de métadonnées d'initialisation de champ. Un littéral conforme à CLS doit avoir une valeur spécifiée dans les métadonnées d'initialisation de champ qui est exactement du même type que le littéral (ou du type sous-jacent, si ce littéral est une `enum`).|13|
|Membres|[Membres de types en général](#members)|La contrainte vararg ne fait pas partie de la spécification CLS, et la seule convention d’appel prise en charge par la spécification CLS est la convention d’appel managée standard.|15|
|Conventions d’affectation de noms|[Conventions de nommage](#naming)|Les assemblys doivent suivre l’Annexe 7 du Rapport technique 15 du standard Unicode 3.0 régissant l’ensemble des caractères autorisés au début et dans les identificateurs. Cette annexe est disponible en ligne à l’adresse <https://www.unicode.org/unicode/reports/tr15/tr15-18.html>. Les identificateurs doivent être dans un format canonique défini par la forme C de normalisation Unicode. Dans le cadre de la spécification CLS, deux identificateurs sont les mêmes si leurs mappages en minuscules (comme spécifié par les mappages en minuscules un-à-un insensibles aux paramètres régionaux Unicode) sont identiques. Autrement dit, pour que deux identificateurs soient considérés comme différents dans le cadre de la spécification CLS, ils doivent être différenciés par d’autres éléments que leur casse. Toutefois, pour remplacer une définition héritée, l’infrastructure CLI nécessite l’utilisation de l’encodage exact de la déclaration d’origine.|4|
|Surcharge|[Conventions de nommage](#naming)|Tous les noms introduits dans une portée conforme CLS doivent être distincts, indépendamment de leur type, sauf quand les noms sont identiques et résolus par surcharge. Par exemple, alors que CTS autorise un type à utiliser le même nom pour une méthode et un champ, CLS ne l'autorise pas.|5|
|Surcharge|[Conventions de nommage](#naming)|Les champs et les types imbriqués seront distincts par comparaison d'identificateurs seule, même si CTS autorise la distinction de signatures différentes. Les méthodes, les propriétés et les événements qui portent le même nom (par comparaison d’identificateurs) doivent différer par d’autres éléments que le seul type de retour, sauf dans les cas spécifiés dans la règle 39 de la spécification CLS.|6|
|Surcharge|[Overloads](#overloads)|Seules les propriétés et les méthodes peuvent être surchargées.|37|
|Surcharge|[Overloads](#overloads)|Les propriétés et les méthodes peuvent être surchargées en fonction du nombre et des types de leurs paramètres uniquement, à l'exception des opérateurs de conversion nommés `op_Implicit` et `op_Explicit`, qui peuvent également être surchargés selon leur type de retour.|38|
|Surcharge|--|Si deux ou plusieurs méthodes conformes CLS déclarées dans un type ont le même nom et, pour un jeu spécifique d’instanciations de types, ont le même paramètre et les mêmes types de retour, alors toutes ces méthodes sont sémantiquement équivalentes à ces instanciations de type.|48|
|Types|[Types et signatures de membres de types](#Types)|<xref:System.Object?displayProperty=nameWithType> est conforme à CLS. Toute autre classe conforme à CLS héritera d'une classe conforme à CLS.|23|
|Propriétés|[Propriétés](#properties)|Les méthodes qui implémentent les méthodes getter et setter d’une propriété doivent être marquées `SpecialName` dans les métadonnées.|24|
|Propriétés|[Propriétés](#properties)|Les accesseurs d’une propriété devront tous être statiques, virtuels ou être des instances.|26|
|Propriétés|[Propriétés](#properties)|Le type d’une propriété devra correspondre au type de retour de la méthode getter et au type du dernier argument de la méthode setter. Les types des paramètres de la propriété devront correspondre aux types des paramètres de la méthode getter et aux types de tous les paramètres de la méthode setter, sauf le dernier. Tous ces types devront être conformes à CLS et ne pas être des pointeurs managés (à savoir, ils ne doivent pas être passés par référence).|27|
|Propriétés|[Propriétés](#properties)|Les propriétés adhéreront à un modèle d’attribution de nom spécifique. L'attribut `SpecialName` dont il est question dans la règle 24 de la spécification CLS sera ignoré dans les comparaisons de noms appropriées et respectera les règles d'identificateur. Une propriété aura une méthode getter, une méthode setter ou les deux.|28|
|Conversion de type|[Conversion de type](#conversion)|Si `op_Implicit` ou `op_Explicit` est fourni, un autre moyen sera utilisé pour fournir la contrainte.|39|
|Types|[Types et signatures de membres de types](#Types)|Les types de valeurs encadrés ne sont pas conformes à CLS.|3|
|Types|[Types et signatures de membres de types](#Types)|Tous les types apparaissant dans une signature devront être conformes à CLS. Tous les types composant un type générique instancié devront être conformes à CLS.|11|
|Types|[Types et signatures de membres de types](#Types)|Les références typées ne sont pas conformes CLS.|14|
|Types|[Types et signatures de membres de types](#Types)|Les types de pointeurs non managés ne sont pas conformes à CLS.|17|
|Types|[Types et signatures de membres de types](#Types)|Les classes, les types de valeurs et les interfaces conformes à CLS ne nécessiteront pas l'implémentation de membres non conformes à CLS.|20|

<a name="Types"></a>

### <a name="types-and-type-member-signatures"></a>Types et signatures de membres de types

Le type <xref:System.Object?displayProperty=nameWithType> est conforme à CLS et correspond au type de base de tous les types d'objets du système de types du .Net Framework. Dans le .NET Framework, l'héritage est implicite (par exemple, la classe <xref:System.String> hérite implicitement de la classe <xref:System.Object> ) ou explicite (par exemple, la classe <xref:System.Globalization.CultureNotFoundException> hérite explicitement de la classe <xref:System.ArgumentException>, qui hérite explicitement de la classe <xref:System.SystemException>, qui hérite explicitement de la classe <xref:System.Exception>). Pour qu'un type dérivé soit conforme à CLS, son type de base doit également être conforme à CLS.

L'exemple suivant montre un type dérivé dont le type de base n'est pas conforme à CLS. Il définit une classe `Counter` de base qui utilise un entier 32 bits non signé en tant que compteur. La classe fournissant une fonctionnalité de compteur en encapsulant un entier non signé, elle est marquée comme non conforme à CLS. Par conséquent, une classe dérivée, `NonZeroCounter`, n'est pas non plus conforme à CLS.

[!code-csharp[Conceptual.CLSCompliant#12](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type3.cs#12)]
[!code-vb[Conceptual.CLSCompliant#12](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type3.vb#12)]

Tous les types qui apparaissent dans les signatures de membres, notamment le type de retour d’une méthode ou un type de propriété, doivent être conformes à CLS. En outre, pour les types génériques :

- Tous les types qui composent un type générique instancié doivent être conformes à CLS.

- Tous les types utilisés comme contraintes sur des paramètres génériques doivent eux-mêmes être conformes à CLS.

Le [système de type commun](../../docs/standard/base-types/common-type-system.md) (CTS, Common Type System) du .NET Framework inclut un certain nombre de types intégrés pris en charge directement par le Common Langage Runtime et qui sont spécialement encodés dans les métadonnées d'un assembly. Parmi les types intrinsèques, les types répertoriés dans le tableau suivant sont conformes à CLS.

|Type conforme à CLS|Description|
|-------------------------|-----------------|
|<xref:System.Byte>|Entier 8 bits non signé|
|<xref:System.Int16>|Entier 16 bits signé|
|<xref:System.Int32>|Entier 32 bits signé|
|<xref:System.Int64>|Entier 64 bits signé|
|<xref:System.Single>|Valeur à virgule flottante simple précision|
|<xref:System.Double>|Valeur à virgule flottante double précision|
|<xref:System.Boolean>|Type de valeur `true` ou `false`|
|<xref:System.Char>|Unité de code encodée en UTF-16|
|<xref:System.Decimal>|Nombre décimal à virgule fixe|
|<xref:System.IntPtr>|Pointeur ou handle d'une taille définie par la plateforme|
|<xref:System.String>|Collection de zéro, un ou plusieurs objets <xref:System.Char>|

Les types intrinsèques répertoriés dans le tableau suivant ne sont pas conformes à CLS.

|Type non conforme|Description|Alternative conforme à CLS|
|-------------------------|-----------------|--------------------------------|
|<xref:System.SByte>|Type de données entier signé 8 bits|<xref:System.Int16>|
|<xref:System.TypedReference>|Pointeur vers un objet et son type au moment de l'exécution|None|
|<xref:System.UInt16>|Entier 16 bits non signé|<xref:System.Int32>|
|<xref:System.UInt32>|Entier non signé 32 bits|<xref:System.Int64>|
|<xref:System.UInt64>|Entier non signé 64 bits|<xref:System.Int64> (peut dépasser la capacité), <xref:System.Numerics.BigInteger> ou <xref:System.Double>|
|<xref:System.UIntPtr>|Pointeur ou handle non signé|<xref:System.IntPtr>|

La bibliothèque de classes du .NET Framework ou toute autre bibliothèque de classes peut inclure d'autres types non conformes à CLS. Par exemple :

- Types de valeurs encadrés. L'exemple C# suivant crée une classe qui a une propriété publique de type `int*` nommée `Value`. Comme `int*` est un type de valeur encadré, le compilateur le signale comme non conforme à CLS.

  [!code-csharp[Conceptual.CLSCompliant#26](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/box2.cs#26)]

- Références typées, qui sont des constructions spéciales qui contiennent une référence à un objet et une référence à un type. Les références typées sont représentées dans le .NET Framework par la classe <xref:System.TypedReference>.

Si un type n'est pas conforme à CLS, vous devez lui appliquer l'attribut <xref:System.CLSCompliantAttribute> avec une valeur `isCompliant` de `false`. Pour plus d’informations, voir La section [d’attributs CLSCompliantAttribute.](#CLSAttribute)

L'exemple suivant illustre le problème de conformité CLS dans une signature de méthode et dans une instanciation de type générique. Il définit une classe `InvoiceItem` avec une propriété de type <xref:System.UInt32>, une propriété de type `Nullable(Of UInt32)` et un constructeur avec les paramètres de type <xref:System.UInt32> et `Nullable(Of UInt32)`. Vous obtenez quatre avertissements du compilateur lorsque vous essayez de compiler cet exemple.

[!code-csharp[Conceptual.CLSCompliant#3](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type1.cs#3)]
[!code-vb[Conceptual.CLSCompliant#3](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type1.vb#3)]

Pour supprimer les avertissements du compilateur, remplacez les types non conforme à CLS de l'interface publique `InvoiceItem` par des types conformes :

[!code-csharp[Conceptual.CLSCompliant#4](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/type2.cs#4)]
[!code-vb[Conceptual.CLSCompliant#4](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/type2.vb#4)]

Outre les types spécifiques répertoriés, certaines catégories de types ne sont pas conformes à CLS. Celles-ci incluent les types de pointeurs non managés et les types de pointeurs de fonctions. L'exemple suivant génère un avertissement du compilateur, car il utilise un pointeur vers un entier pour créer un tableau d'entiers.

[!code-csharp[Conceptual.CLSCompliant#5](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/unmanagedptr1.cs#5)]

Pour les classes abstraites conformes à CLS (autrement dit, les classes marquées comme `abstract` en C# ou comme `MustInherit` en Visual Basic), tous les membres de la classe doivent également être conformes à CLS.

<a name="naming"></a>

### <a name="naming-conventions"></a>Conventions d’affectation de noms

Étant donné que certains langages de programmation ne respectent pas la casse, les identificateurs (tels que les noms d'espaces de noms, de types et de membres) doivent se différencier par autre chose que la casse. Deux identificateurs sont considérés comme équivalents si leurs mappages en minuscules sont identiques. L'exemple C# suivant définit deux classes publiques : `Person` et `person`. Étant donné qu'elles ne diffèrent que par leur casse, le compilateur C# les signale comme étant non conformes à CLS.

[!code-csharp[Conceptual.CLSCompliant#16](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#16)]

Les identificateurs de langage de programmation, comme les noms d’espaces de noms, de types et de membres, doivent être conformes au document [Unicode Standard 3.0, Technical Report 15, Annex 7](https://www.unicode.org/reports/tr15/tr15-18.html) (Norme Unicode 3.0, Rapport technique 15, Annexe 7). Cela signifie que :

- Le premier caractère d'un identificateur peut être une lettre majuscule, une lettre minuscule, une initiale majuscule, une lettre de modificateur, une autre lettre ou un nombre sous forme de lettre, Unicode. Pour plus d'informations sur les catégories de caractères Unicode, consultez l'énumération <xref:System.Globalization.UnicodeCategory?displayProperty=nameWithType>.

- Les caractères suivants peuvent provenir de n'importe laquelle des catégories, comme le premier caractère, et peuvent également inclure des marques de non-espacement, des nombres décimaux, des ponctuations de connecteur et des codes de mise en forme.

Avant de comparer les identificateurs, vous devez éliminer par filtrage les codes de mise en forme et convertir les identificateurs au formulaire de normalisation Unicode C, car un caractère unique peut être représenté par plusieurs unités de code encodées en UTF-16. Les séquences de caractères qui produisent les mêmes unités de code dans un formulaire de normalisation Unicode C ne sont pas conformes à CLS. L'exemple suivant définit une propriété nommée `Å`, qui est constituée du caractère SYMBOLE ANGSTRÖM (U+212B), et une deuxième propriété nommée `Å`, qui est constituée du caractère LETTRE MAJUSCULE LATINE A AVEC DIACRITIQUE ROND EN CHEF (U+00C5). Les compilateurs C# et Visual Basic marquent le code source comme non conforme à CLS.

[!code-csharp[Conceptual.CLSCompliant#17](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming1.cs#17)]
[!code-vb[Conceptual.CLSCompliant#17](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming1.vb#17)]

Les noms de membres dans une portée donnée (tels que les espaces de noms dans un assembly, les types dans un espace de noms ou les membres dans un type) doivent être uniques, à l'exception des noms résolus par la surcharge. Cette spécification est plus stricte que celle du système de type commun, qui autorise plusieurs membres d'une portée à avoir des noms identiques tant qu'il s'agit de types de membres différents (par exemple, l'un est une méthode et l'autre est un champ). En particulier, pour les membres de types :

- Les champs et les types imbriqués se distinguent par le nom uniquement.

- Les méthodes, les propriétés et les événements qui portent le même nom doivent différer par autre chose que le type de retour.

L'exemple suivant illustre la spécification selon laquelle les noms de membres doivent être uniques dans leur portée. Il définit une classe nommée `Converter` qui inclut quatre membres nommés `Conversion`. Trois sont des méthodes, le dernier est une propriété. La méthode qui inclut un paramètre <xref:System.Int64> est nommée de manière unique, contrairement aux deux méthodes contenant un paramètre <xref:System.Int32>, car la valeur de retour n'est pas considérée comme faisant partie de la signature d'un membre. La propriété `Conversion` enfreint également cette spécification, car les propriétés ne peuvent pas avoir le même nom que les méthodes surchargées.

[!code-csharp[Conceptual.CLSCompliant#19](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/naming3.cs#19)]
[!code-vb[Conceptual.CLSCompliant#19](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/naming3.vb#19)]

Les langages individuels incluent des mots clés uniques de sorte que les langages qui ciblent le Common Langage Runtime doivent également fournir un mécanisme de référencement des identificateurs (tels que les noms de types) qui coïncident avec les mots clés. Par exemple, `case` est un mot clé en C# et Visual Basic. Toutefois, l'exemple Visual Basic suivant peut supprimer l'ambiguïté entre une classe nommée `case` et le mot clé `case` en utilisant des accolades ouvrantes et fermantes. Sans cela, l'exemple générerait le message d'erreur : « Mot clé non valide en tant qu'identificateur » et échouerait lors de la compilation.

[!code-vb[Conceptual.CLSCompliant#22](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/keyword1.vb#22)]

L'exemple C# suivant peut instancier la classe `case` en utilisant le symbole `@` pour lever l'ambiguïté de l'identificateur par rapport au mot clé de langage. Sans cela, le compilateur C# afficherait deux messages d'erreur : « Type attendu » et « Terme d'expression non valide 'case' ».

[!code-csharp[Conceptual.CLSCompliant#23](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/keyword2.cs#23)]

<a name="conversion"></a>

### <a name="type-conversion"></a>Conversion de type

La spécification CLS (Common Language Specification) définit deux opérateurs de conversion :

- `op_Implicit`, qui est utilisé pour les conversions étendues qui n'entraînent pas la perte de données ou de précision. Par exemple, la structure <xref:System.Decimal> inclut un opérateur `op_Implicit` surchargé pour convertir les valeurs de types intégraux et les valeurs <xref:System.Char> en valeurs <xref:System.Decimal>.

- `op_Explicit`, qui est utilisé pour les conversions restrictives qui peuvent entraîner la perte d'amplitude (une valeur est convertie en une valeur qui entraîne une plus petite plage) ou de précision. Par exemple, la structure <xref:System.Decimal> inclut un opérateur `op_Explicit` surchargé pour convertir les valeurs <xref:System.Double> et <xref:System.Single> en <xref:System.Decimal> et convertir les valeurs <xref:System.Decimal> en valeurs intégrales, <xref:System.Double>, <xref:System.Single> et <xref:System.Char>.

Toutefois, tous les langages ne prennent pas en charge la surcharge d'opérateur ou la définition d'opérateurs personnalisés. Si vous décidez d'implémenter ces opérateurs de conversion, vous devez également fournir une autre façon d'effectuer la conversion. Nous vous recommandons `From`de `To`fournir des méthodes *Xxx* et *Xxx.*

L'exemple suivant définit les conversions implicites et explicites conformes à CLS. Il crée une classe `UDouble` qui représente un nombre à virgule flottante double précision signé. Il s'applique aux conversions implicites de `UDouble` à <xref:System.Double> et aux conversions explicites de `UDouble` à <xref:System.Single>, de <xref:System.Double> à `UDouble` et de <xref:System.Single> à `UDouble`. Il définit également une méthode `ToDouble` comme une alternative à l'opérateur de conversion implicite et les méthodes `ToSingle`, `FromDouble` et `FromSingle` comme alternatives aux opérateurs de conversion explicite.

[!code-csharp[Conceptual.CLSCompliant#15](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/convert1.cs#15)]
[!code-vb[Conceptual.CLSCompliant#15](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/convert1.vb#15)]

<a name="arrays"></a>

### <a name="arrays"></a>Tableaux

Les tableaux conformes à CLS respectent les règles suivantes :

- Toutes les dimensions d'un tableau doivent avoir une limite inférieure égale à zéro. L'exemple suivant crée un tableau non conforme à CLS avec une limite inférieure égale à un. Notez que, malgré la présence de l'attribut <xref:System.CLSCompliantAttribute>, le compilateur ne détecte pas que le tableau retourné par la méthode `Numbers.GetTenPrimes` n'est pas conforme à CLS.

  [!code-csharp[Conceptual.CLSCompliant#8](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array1.cs#8)]
  [!code-vb[Conceptual.CLSCompliant#8](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array1.vb#8)]

- Tous les éléments du tableau doivent se composer de types conformes à CLS. L'exemple suivant définit deux méthodes qui retournent des tableaux non conformes à CLS. La première retourne un tableau de valeurs <xref:System.UInt32>. Le second retourne un tableau <xref:System.Object> qui inclut les valeurs <xref:System.Int32> et <xref:System.UInt32>. Bien que le compilateur identifie le premier tableau comme non conforme en raison de son type <xref:System.UInt32>, il ne parvient pas à reconnaître que le second tableau inclut des éléments non conformes à CLS.

  [!code-csharp[Conceptual.CLSCompliant#9](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array2.cs#9)]
  [!code-vb[Conceptual.CLSCompliant#9](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array2.vb#9)]

- La résolution de surcharge pour les méthodes qui ont des paramètres de tableau repose sur le fait qu’il s’agit de tableaux et sur leur type d’élément. C'est pourquoi la définition suivante d'une méthode `GetSquares` surchargée est conforme à CLS.

  [!code-csharp[Conceptual.CLSCompliant#10](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/array3.cs#10)]
  [!code-vb[Conceptual.CLSCompliant#10](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/array3.vb#10)]

<a name="Interfaces"></a>

### <a name="interfaces"></a>Interfaces

Les interfaces conformes à CLS peuvent définir des propriétés, des événements et des méthodes virtuelles (méthodes sans implémentation). Une interface conforme à CLS ne peut avoir aucune des caractéristiques suivantes :

- Méthodes statiques ou champs statiques. Les compilateurs C# et Visual Basic génèrent des erreurs du compilateur si vous définissez un membre statique dans une interface.

- Champs. Les compilateurs C# et Visual Basic génèrent des erreurs du compilateur si vous définissez un champ dans une interface.

- Méthodes qui ne sont pas conformes à CLS. Par exemple, la définition d'interface suivante inclut une méthode, `INumber.GetUnsigned`, qui est marquée comme non conforme à CLS. Cet exemple génère un avertissement du compilateur.

  [!code-csharp[Conceptual.CLSCompliant#6](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/interface2.cs#6)]
  [!code-vb[Conceptual.CLSCompliant#6](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/interface2.vb#6)]

  En raison de cette règle, pour implémenter des membres non conformes à CLS, il n'est pas nécessaire d'utiliser des types conformes à CLS. Si une infrastructure conforme à CLS expose une classe qui implémente une interface non conforme à CLS, elle doit également fournir des implémentations concrètes de tous les membres non conformes.

Les compilateurs de langages conformes à CLS doivent également permettre à une classe de fournir des implémentations séparées des membres qui ont les mêmes nom et signature dans plusieurs interfaces.  C# et Visual Basic prennent en charge des [implémentations d’interface explicites](../csharp/programming-guide/interfaces/explicit-interface-implementation.md) pour fournir des implémentations différentes de méthodes portant le même nom. Visual Basic prend également en charge le mot clé `Implements`, qui vous permet de désigner explicitement l'interface et le membre implémentés par un membre particulier. L'exemple suivant illustre ce scénario en définissant une classe `Temperature` qui implémente les interfaces `ICelsius` et `IFahrenheit` en tant qu'implémentations d'interface explicites.

[!code-csharp[Conceptual.CLSCompliant#24](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/eii1.cs#24)]
[!code-vb[Conceptual.CLSCompliant#24](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/eii1.vb#24)]

<a name="enums"></a>

### <a name="enumerations"></a>Énumérations

Les énumérations conformes à CLS doivent suivre ces règles :

- Le type sous-jacent de l'énumération doit être un entier conforme à CLS intrinsèque (<xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32> ou <xref:System.Int64>). Par exemple, le code suivant tente de définir une énumération dont le type sous-jacent est <xref:System.UInt32> et génère un avertissement du compilateur.

  [!code-csharp[Conceptual.CLSCompliant#7](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/enum3.cs#7)]
  [!code-vb[Conceptual.CLSCompliant#7](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/enum3.vb#7)]

- Un type d'énumération doit avoir un champ d'instance unique nommé `Value__` qui est marqué avec l'attribut <xref:System.Reflection.FieldAttributes.RTSpecialName?displayProperty=nameWithType>. Cela vous permet de référencer implicitement la valeur du champ.

- Une énumération inclut les champs statiques littéraux du même type que l'énumération elle-même. Par exemple, si vous définissez une énumération `State` avec les valeurs `State.On` et `State.Off`, `State.On` et `State.Off` sont les deux champs statiques littéraux dont le type est `State`.

- Il existe deux types d'énumérations :

  - Une énumération qui représente un jeu de valeurs entières nommées qui s'excluent mutuellement. Ce type d'énumération est indiqué par l'absence de l'attribut personnalisé <xref:System.FlagsAttribute?displayProperty=nameWithType>.

  - Une énumération qui représente un jeu d'indicateurs binaires qui peuvent être combinés pour générer une valeur sans nom. Ce type d'énumération est indiqué par la présence de l'attribut personnalisé <xref:System.FlagsAttribute?displayProperty=nameWithType>.

  Pour plus d'informations, consultez la documentation de la structure <xref:System.Enum>.

- La valeur d'une énumération ne se limite pas à la plage de ses valeurs spécifiées. En d'autres termes, la plage de valeurs d'une énumération est la plage de sa valeur sous-jacente. Vous pouvez utiliser la méthode <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> pour déterminer si une valeur spécifiée est membre d'une énumération.

<a name="members"></a>

### <a name="type-members-in-general"></a>Membres de types en général

La spécification CLS (Common Language Specification) nécessite que tous les champs et toutes les méthodes soient accessibles en tant que membres d'une classe particulière. Par conséquent, les méthodes et les champs statiques globaux (autrement dit, les méthodes ou les champs statiques définis en dehors d'un type) ne sont pas conformes à CLS. Si vous essayez d'inclure un champ global ou une méthode globale dans votre code source, les compilateurs C# et Visual Basic génèrent une erreur de compilateur.

La spécification CLS (Common Language Specification) prend uniquement en charge la convention d'appel managée standard. Elle ne prend pas en charge les conventions d'appel non managées ni les méthodes avec des listes d'arguments variables marquées avec le mot clé `varargs`. Pour les listes d’arguments variables compatibles avec la convention d’appel managée standard, utilisez l’attribut <xref:System.ParamArrayAttribute> ou l’implémentation de chaque langage, telle que le mot clé `params` en C# et le mot clé `ParamArray` en Visual Basic.

<a name="MemberAccess"></a>

### <a name="member-accessibility"></a>Accessibilité des membres

Le remplacement d'un membre hérité ne peut pas modifier l'accessibilité de ce membre. Par exemple, une méthode publique dans une classe de base ne peut pas être remplacée par une méthode privée dans une classe dérivée. Il existe une exception : un membre `protected internal` (en C#) ou `Protected Friend` (en Visual Basic) dans un assembly qui est remplacé par un type dans un autre assembly. Dans ce cas, l'accessibilité du remplacement est `Protected`.

L'exemple suivant illustre l'erreur générée lorsque l'attribut <xref:System.CLSCompliantAttribute> a la valeur `true`, et que `Human`, qui est une classe dérivée de `Animal`, essaie de remplacer l'accessibilité publique de la propriété `Species` par une accessibilité privée. L'exemple se compile correctement si son accessibilité devient publique.

[!code-csharp[Conceptual.CLSCompliant#28](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility1.cs#28)]
[!code-vb[Conceptual.CLSCompliant#28](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility1.vb#28)]

Les types de la signature d'un membre doivent être accessibles chaque fois que ce membre est accessible. Par exemple, cela signifie qu'un membre public ne peut pas inclure un paramètre dont le type est privé, protégé ou interne. L'exemple suivant illustre l'erreur de compilateur obtenue lorsqu'un constructeur de classe `StringWrapper` expose une valeur d'énumération `StringOperationType` interne qui détermine comment une valeur de chaîne doit être encapsulée.

[!code-csharp[Conceptual.CLSCompliant#27](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/accessibility3.cs#27)]
[!code-vb[Conceptual.CLSCompliant#27](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/accessibility3.vb#27)]

<a name="Generics"></a>

### <a name="generic-types-and-members"></a>Types et membres génériques

Les types imbriqués ont toujours au moins autant de paramètres génériques que leur type englobant. Ceux-ci correspondent par position aux paramètres génériques du type englobant. Le type générique peut également inclure de nouveaux paramètres génériques.

La relation entre les paramètres de type générique d'un type conteneur et ses types imbriqués peut être masquée par la syntaxe des différents langages. Dans l'exemple suivant, un type générique `Outer<T>` contient deux classes imbriquées, `Inner1A` et `Inner1B<U>`. Les appels à la méthode `ToString`, dont chaque classe hérite de <xref:System.Object.ToString%2A?displayProperty=nameWithType>, indiquent que chaque classe imbriquée inclut les paramètres de type de sa classe conteneur.

[!code-csharp[Conceptual.CLSCompliant#29](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/nestedgenerics2.cs#29)]
[!code-vb[Conceptual.CLSCompliant#29](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/nestedgenerics2.vb#29)]

Les noms de type génériques sont codés dans le \` *nom\`de*forme n , où le *nom* est le nom de type, est un personnage littéral, et *n* est le nombre de paramètres déclarés sur le type, ou, pour les types génériques imbriqués, le nombre de paramètres de type nouvellement introduits. Cet encodage de noms de types génériques intéresse principalement les développeurs qui utilisent la réflexion pour accéder aux types génériques conformes à CLS dans une bibliothèque.

Si les contraintes sont appliquées à un type générique, tous les types utilisés en tant que contraintes doivent également être conformes à CLS. L'exemple suivant définit une classe nommée `BaseClass` qui n'est pas conforme à CLS et une classe générique nommée `BaseCollection` dont le paramètre de type doit dériver de `BaseClass`. Toutefois, comme `BaseClass` n'est pas conforme à CLS, le compilateur émet un avertissement.

[!code-csharp[Conceptual.CLSCompliant#34](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics5.cs#34)]
[!code-vb[Conceptual.CLSCompliant#34](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics5.vb#34)]

Si un type générique est dérivé d'un type de base générique, il doit redéclarer toutes les contraintes pour s'assurer que les contraintes du type de base sont également satisfaites. L'exemple suivant définit un `Number<T>` qui peut représenter un type numérique. Il définit également une classe `FloatingPoint<T>` qui représente une valeur à virgule flottante. Toutefois, le code source ne se compile pas, car il n'applique pas la contrainte `Number<T>` (ce T doit être un type de valeur) à `FloatingPoint<T>`.

[!code-csharp[Conceptual.CLSCompliant#30](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2a.cs#30)]
[!code-vb[Conceptual.CLSCompliant#30](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2a.vb#30)]

L'exemple se compile correctement si la contrainte est ajoutée à la classe `FloatingPoint<T>`.

[!code-csharp[Conceptual.CLSCompliant#31](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics2.cs#31)]
[!code-vb[Conceptual.CLSCompliant#31](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics2.vb#31)]

La spécification CLS (Common Language Specification) impose un modèle conservateur par instanciation pour les types imbriqués et les membres protégés. Les types génériques ouverts ne peuvent pas exposer de champs ou de membres avec des signatures qui contiennent une instanciation spécifique d'un type générique imbriqué et protégé. Les types non génériques qui étendent une instanciation spécifique d'une classe de base ou une interface générique ne peuvent pas exposer de champs ou de membres avec des signatures qui contiennent une instanciation différente d'un type générique imbriqué et protégé.

L'exemple suivant définit un type générique, `C1<T>` (ou `C1(Of T)` en Visual Basic) et une classe protégée, `C1<T>.N` (ou `C1(Of T).N` en Visual Basic). `C1<T>` a deux méthodes : `M1` et `M2`. Toutefois, `M1` n’est pas conforme CLS parce qu’elle essaie de retourner un objet `C1<int>.N` (ou `C1(Of Integer).N`) depuis C1\<T> (ou `C1(Of T)`). Une deuxième classe, `C2`, est dérivée de `C1<long>` (ou de `C1(Of Long)`). Elle a deux méthodes, `M3` et `M4`. `M3` n'est pas conforme à CLS parce qu'elle essaie de retourner un objet `C1<int>.N` (ou `C1(Of Integer).N`) d'une sous-classe de `C1<long>`. Notez que les compilateurs de langage peuvent être encore plus restrictifs. Dans cet exemple, Visual Basic affiche une erreur lorsqu'il tente de compiler `M4`.

[!code-csharp[Conceptual.CLSCompliant#32](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/generics4.cs#32)]
[!code-vb[Conceptual.CLSCompliant#32](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/generics4.vb#32)]

<a name="ctors"></a>

### <a name="constructors"></a>Constructeurs

Les constructeurs des classes et structures conformes à CLS doivent suivre ces règles :

- Un constructeur d'une classe dérivée doit appeler le constructeur d'instance de sa classe de base avant d'accéder aux données d'instance héritées. Cette spécification est due au fait que les constructeurs de classes de base ne sont pas hérités par leurs classes dérivées. Cette règle ne s'applique pas aux structures, qui ne prennent pas en charge l'héritage direct.

  En général, les compilateurs appliquent cette règle indépendamment de la conformité CLS, comme indiqué dans l'exemple suivant. Il crée une classe `Doctor` dérivée d'une classe `Person`, mais la classe `Doctor` ne parvient pas à appeler le constructeur de classe `Person` pour initialiser les champs d'instance hérités.

  [!code-csharp[Conceptual.CLSCompliant#11](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/ctor1.cs#11)]
  [!code-vb[Conceptual.CLSCompliant#11](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/ctor1.vb#11)]

- Un constructeur d'objet ne peut être appelé que pour créer un objet. En outre, un objet ne peut pas être initialisé deux fois. Par exemple, cela signifie que <xref:System.Object.MemberwiseClone%2A?displayProperty=nameWithType> et les méthodes de désérialisation telles que <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> ne doivent pas appeler de constructeurs.

<a name="properties"></a>

### <a name="properties"></a>Propriétés

Les propriétés dans les types conformes à CLS doivent suivre ces règles :

- Une propriété doit posséder une méthode setter, getter ou les deux. Dans un assembly, celles-ci sont implémentées comme des méthodes spéciales, ce qui signifie qu’elles apparaîtront comme des méthodes distinctes (la méthode getter est nommée `get_`*propertyname* et la méthode setter est nommée `set_`*propertyname*) marquées comme `SpecialName` dans les métadonnées de l’assembly. Les compilateurs C# et Visual Basic appliquent automatiquement cette règle sans qu'il soit nécessaire d'appliquer l'attribut <xref:System.CLSCompliantAttribute>.

- Le type d’une propriété correspond au type de retour de la méthode getter de la propriété et du dernier argument de la méthode setter. Ces types doivent être conformes à CLS et les arguments ne peuvent pas être assignés à la propriété par référence (autrement dit, ils ne peuvent pas être des pointeurs managés).

- Si une propriété possède une méthode getter et une méthode setter, elles doivent être toutes les deux virtuelles, statiques ou être toutes les deux des instances. Les compilateurs C# et Visual Basic appliquent automatiquement cette règle via leur syntaxe de définition de propriété.

<a name="events"></a>

### <a name="events"></a>Événements

Un événement est défini par son nom et son type. Le type d'événement est un délégué utilisé pour indiquer l'événement. Par exemple, l'événement <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> est de type <xref:System.ResolveEventHandler>. Outre l'événement lui-même, trois méthodes avec des noms basés sur le nom de l'événement fournissent une implémentation de l'événement et sont marquées comme `SpecialName` dans les métadonnées de l'assembly :

- Une méthode pour ajouter un `add_`gestionnaire d’événements, nommé *EventName*. Par exemple, la méthode d'abonnement aux événements pour l'événement <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> est nommée `add_AssemblyResolve`.

- Une méthode pour supprimer un `remove_`gestionnaire d’événements, nommé *EventName*. Par exemple, la méthode de suppression pour l'événement <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> est nommée `remove_AssemblyResolve`.

- Une méthode pour indiquer que l’événement s’est produit, nommée `raise_`*NomÉvénement*.

> [!NOTE]
> La plupart des règles de la spécification CLS concernant les événements sont implémentées par les compilateurs de langage et sont transparentes aux développeurs de composants.

L'accessibilité des méthodes permettant d'ajouter, de supprimer et de déclencher un événement doit être identique. Les méthodes doivent également toutes être statiques, instanciées ou virtuelles. Les méthodes d'ajout et de suppression d'un événement ont un paramètre dont le type est le type du délégué d'événement. Les méthodes d'ajout et de suppression doivent être toutes les deux présentes ou absentes.

L'exemple suivant définit une classe conforme à CLS nommée `Temperature` qui déclenche un événement `TemperatureChanged` si le changement de température entre deux lectures est égal ou supérieur à une valeur seuil. La classe `Temperature` définit explicitement une méthode `raise_TemperatureChanged` afin de pouvoir exécuter de manière sélective les gestionnaires d'événements.

[!code-csharp[Conceptual.CLSCompliant#20](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/event1.cs#20)]
[!code-vb[Conceptual.CLSCompliant#20](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/event1.vb#20)]

<a name="overloads"></a>

### <a name="overloads"></a>Overloads

La spécification CLS impose les conditions suivantes aux membres surchargés :

- Les membres peuvent être surchargés selon le nombre de paramètres et le type d'un paramètre. La convention d’appel, le type de retour, les modificateurs personnalisés appliqués à la méthode ou à son paramètre et le fait que les paramètres soient transmis par valeur ou par référence ne sont pas pris en considération lors de la différenciation des surcharges. Pour obtenir un exemple, consultez le code de l’exigence indiquant que les noms doivent être uniques dans une portée, dans la section [Conventions d’affectation de noms](#naming).

- Seules les propriétés et les méthodes peuvent être surchargées. Les champs et les événements ne peuvent pas être surchargés.

- Les méthodes génériques peuvent être surchargées selon le nombre de leurs paramètres génériques.

> [!NOTE]
> Les opérateurs `op_Explicit` et `op_Implicit` sont des exceptions à la règle indiquant que la valeur de retour n'est pas considérée comme faisant partie d'une signature de méthode pour la résolution de la surcharge. Ces deux opérateurs peuvent être surchargés selon leurs paramètres et leur valeur de retour.

<a name="exceptions"></a>

### <a name="exceptions"></a>Exceptions

Les objets d'exception doivent dériver de <xref:System.Exception?displayProperty=nameWithType> ou d'un autre type dérivé de <xref:System.Exception?displayProperty=nameWithType>. L'exemple suivant illustre l'erreur de compilateur obtenue lorsqu'une classe personnalisée nommée `ErrorClass` est utilisée pour la gestion des exceptions.

[!code-csharp[Conceptual.CLSCompliant#13](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions1.cs#13)]
[!code-vb[Conceptual.CLSCompliant#13](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions1.vb#13)]

Pour corriger cette erreur, la classe `ErrorClass` doit hériter de <xref:System.Exception?displayProperty=nameWithType>. En outre, la propriété `Message` doit être remplacée. L'exemple suivant corrige ces erreurs pour définir une classe `ErrorClass` conforme à CLS.

[!code-csharp[Conceptual.CLSCompliant#14](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/exceptions2.cs#14)]
[!code-vb[Conceptual.CLSCompliant#14](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/exceptions2.vb#14)]

<a name="attributes"></a>

### <a name="attributes"></a>Attributs

Dans les assemblys .NET Framework, les attributs personnalisés fournissent un mécanisme extensible pour stocker des attributs personnalisés et récupérer les métadonnées concernant la programmation des objets, tels que les assemblys, les types, les membres et les paramètres de méthode. Les attributs personnalisés doivent dériver de <xref:System.Attribute?displayProperty=nameWithType> ou d'un type dérivé de <xref:System.Attribute?displayProperty=nameWithType>.

L'exemple suivant enfreint cette règle. Il définit une classe `NumericAttribute` qui ne dérive pas de <xref:System.Attribute?displayProperty=nameWithType>. Notez qu'une erreur du compilateur se produit uniquement lorsque l'attribut non conforme à CLS est appliqué, pas lorsque la classe est définie.

[!code-csharp[Conceptual.CLSCompliant#18](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/attribute1.cs#18)]
[!code-vb[Conceptual.CLSCompliant#18](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/attribute1.vb#18)]

Le constructeur ou les propriétés d'un attribut conforme à CLS peuvent exposer uniquement les types suivants :

- <xref:System.Boolean>

- <xref:System.Byte>

- <xref:System.Char>

- <xref:System.Double>

- <xref:System.Int16>

- <xref:System.Int32>

- <xref:System.Int64>

- <xref:System.Single>

- <xref:System.String>

- <xref:System.Type>

- Tout type d'énumération dont le type sous-jacent est <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32> ou <xref:System.Int64>.

L'exemple suivant définit une classe `DescriptionAttribute` qui dérive de <xref:System.Attribute>. Le constructeur de classe a un paramètre de type `Descriptor`, la classe n'est donc pas conforme à CLS. Notez que le compilateur C# émet un avertissement mais compile correctement, alors que le compilateur Visual Basic n'émet ni avertissement ni erreur.

[!code-csharp[Conceptual.CLSCompliant#33](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/attribute2.cs#33)]
[!code-vb[Conceptual.CLSCompliant#33](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/attribute2.vb#33)]

<a name="CLSAttribute"></a>

## <a name="the-clscompliantattribute-attribute"></a>Attribut CLSCompliantAttribute

L'attribut <xref:System.CLSCompliantAttribute> permet d'indiquer si un élément de programme est conforme à la spécification CLS (Common Language Specification). Le constructeur <xref:System.CLSCompliantAttribute.%23ctor%28System.Boolean%29?displayProperty=nameWithType> inclut un seul paramètre obligatoire, `isCompliant`, qui indique si l'élément de programme est conforme à CLS.

Au moment de la compilation, le compilateur détecte les éléments non conformes qui sont présumés conformes à CLS et émet alors un avertissement. Le compilateur n'émet pas d'avertissements pour les types ou les membres qui sont explicitement déclarés comme étant non conformes.

Les développeurs de composants peuvent utiliser l'attribut <xref:System.CLSCompliantAttribute> de deux façons :

- Pour définir les parties de l'interface publique exposées par un composant qui sont conformes à CLS et celles qui ne sont pas conformes à CLS. Lorsque l'attribut est utilisé pour marquer des éléments de programme particuliers comme étant conformes à CLS, son utilisation garantit que ces éléments sont accessibles à partir de tous les langages et outils qui ciblent le .NET Framework.

- Pour vérifier que l'interface publique de la bibliothèque de composants expose uniquement les éléments de programme conformes à CLS. Si les éléments ne sont pas conformes à CLS, les compilateurs publieront généralement un avertissement.

> [!WARNING]
> Dans certains cas, les compilateurs de langages imposent les règles conformes à CLS que l'attribut <xref:System.CLSCompliantAttribute> soit utilisé ou non. Par exemple, définir un membre statique dans une interface viole une règle CLS. À cet égard, si vous définissez un membre `static` (en C#) ou `Shared` (en Visual Basic) dans une interface, les compilateurs C# et Visual Basic affichent un message d'erreur et ne parviennent pas à compiler l'application.

L'attribut <xref:System.CLSCompliantAttribute> est marqué avec un attribut <xref:System.AttributeUsageAttribute> qui a la valeur <xref:System.AttributeTargets.All?displayProperty=nameWithType>. Cette valeur permet d'appliquer l'attribut <xref:System.CLSCompliantAttribute> à un élément de programme, notamment aux assemblys, modules, types (classes, structures, énumérations, interfaces et délégués), membres de types (constructeurs, méthodes, propriétés, champs et événements), paramètres, paramètres génériques et valeurs de retour. Toutefois, dans la pratique, vous devez appliquer l'attribut uniquement aux assemblys, aux types et aux membres de types. Sinon, les compilateurs ignorent l'attribut et continuent à générer des avertissements de compilateur lorsqu'ils rencontrent un paramètre non conforme, un paramètre générique ou une valeur de retour dans l'interface publique de votre bibliothèque.

La valeur de l'attribut <xref:System.CLSCompliantAttribute> est héritée par les éléments de programme contenus. Par exemple, si un assembly est marqué comme étant conforme à CLS, ses types sont également conformes à CLS. Si un type est marqué comme étant conforme à CLS, ses membres et types imbriqués seront également conformes à CLS.

Vous pouvez remplacer explicitement la conformité héritée en appliquant l'attribut <xref:System.CLSCompliantAttribute> à un élément de programme contenu. Par exemple, vous pouvez utiliser l'attribut <xref:System.CLSCompliantAttribute> avec une valeur `isCompliant``false` pour définir un type non conforme dans un assembly conforme et vous pouvez utiliser l'attribut avec une valeur `isCompliant``true` pour définir un type conforme dans un assembly non conforme. Vous pouvez également définir des membres non conformes dans un type conforme. Toutefois, un type non conforme ne peut pas avoir de membres conformes, vous ne pouvez pas utiliser l'attribut avec une valeur `isCompliant``true` pour remplacer l'héritage d'un type non conforme.

Lorsque vous développez des composants, vous devez toujours utiliser l'attribut <xref:System.CLSCompliantAttribute> pour indiquer si votre assembly, ses types et ses membres sont conformes à CLS.

Pour créer des composants conformes à CLS :

1. Utilisez <xref:System.CLSCompliantAttribute> pour marquer votre assembly comme étant conforme à CLS.

2. Marquez les types exposés publiquement de l'assembly qui ne sont pas conformes à CLS comme non conformes.

3. Marquez tous les membres exposés publiquement dans des types conformes à CLS comme non conformes.

4. Fournissez une alternative conforme à CLS pour les membres non conformes.

Si vous avez correctement marqué tous vos types et membres non conformes, le compilateur ne doit émettre aucun avertissement de non-conformité. Toutefois, vous devez indiquer quels membres ne sont pas conformes à CLS et répertorier leurs alternatives conformes à CLS dans votre documentation produit.

L'exemple suivant utilise l'attribut <xref:System.CLSCompliantAttribute> pour définir un assembly conforme à CLS et un type, `CharacterUtilities`, qui a deux membres non conformes à CLS. Les deux membres étant référencés avec l'attribut `CLSCompliant(false)`, le compilateur ne génère aucun avertissement. La classe fournit également une alternative conforme à CLS pour les deux méthodes. Normalement, nous ajouterions seulement deux surcharges à la méthode `ToUTF16` pour fournir des alternatives conformes à CLS. Toutefois, les méthodes ne pouvant pas être surchargées selon la valeur de retour, les noms des méthodes conformes à CLS sont différents des noms des méthodes non conformes.

[!code-csharp[Conceptual.CLSCompliant#35](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.clscompliant/cs/indicator3.cs#35)]
[!code-vb[Conceptual.CLSCompliant#35](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.clscompliant/vb/indicator3.vb#35)]

Si vous développez une application plutôt qu'une bibliothèque (autrement dit, si vous n'exposez pas des types ou des membres qui peuvent être utilisés par d'autres développeurs d'applications), la conformité CLS des éléments de programme que votre application consomme n'a d'intérêt que si votre langage ne les prend pas en charge. Dans ce cas, votre compilateur de langage générera une erreur lorsque vous essaierez d'utiliser un élément non conforme à CLS.

<a name="CrossLang"></a>

## <a name="cross-language-interoperability"></a>Interopérabilité interlangage

L'indépendance du langage a plusieurs significations possibles. Une des significations, qui est décrite dans l’article [Indépendance du langage et composants indépendants du langage](../../docs/standard/language-independence-and-language-independent-components.md), implique la consommation en toute transparence des types écrits dans un langage à partir d’une application écrite dans un autre langage. Une deuxième signification, qui est le sujet de cet article, consiste à combiner du code écrit dans plusieurs langages dans un même assembly .NET Framework.

L'exemple suivant illustre l'interopérabilité interlangage en créant une bibliothèque de classes nommée Utilities.dll qui comprend deux classes, `NumericLib` et `StringLib`. La classe `NumericLib` est écrite en C# et la classe `StringLib` est écrite en Visual Basic. Voici le code source de StringUtil.vb, qui comprend un seul membre, `ToTitleCase`, dans sa `StringLib`.

[!code-vb[Conceptual.CrossLanguage#1](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.crosslanguage/vb/stringutil.vb#1)]

Voici le code source de NumberUtil.cs, qui définit une classe `NumericLib` qui a deux membres, `IsEven` et `NearZero`.

[!code-csharp[Conceptual.CrossLanguage#2](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.crosslanguage/cs/numberutil.cs#2)]

Pour placer les deux classes dans un même assembly, vous devez les compiler dans des modules. Pour compiler le fichier de code source Visual Basic dans un module, utilisez cette commande :

```console
vbc /t:module StringUtil.vb
```

Pour plus d’informations sur la syntaxe de la ligne de commande du compilateur Visual Basic, consultez [Génération à partir de la ligne de commande](../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).

Pour compiler le fichier de code source C# dans un module, utilisez cette commande :

```console
csc /t:module NumberUtil.cs
```

Pour plus d’informations sur la syntaxe de la ligne de commande du compilateur C#, consultez [Génération à partir de la ligne de commande avec csc.exe](../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).

Vous utilisez ensuite les [options de l’éditeur de liens](/cpp/build/reference/linker-options) pour compiler les deux modules en un assembly :

```console
link numberutil.netmodule stringutil.netmodule /out:UtilityLib.dll /dll
```

L'exemple suivant appelle ensuite les méthodes `NumericLib.NearZero` et `StringLib.ToTitleCase`. Notez que le code Visual Basic et le code C# peuvent accéder aux méthodes des deux classes.

[!code-csharp[Conceptual.CrossLanguage#3](../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.crosslanguage/cs/useutilities1.cs#3)]
[!code-vb[Conceptual.CrossLanguage#3](../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.crosslanguage/vb/useutilities1.vb#3)]

Pour compiler le code Visual Basic, utilisez cette commande :

```console
vbc example.vb /r:UtilityLib.dll
```

Pour compiler avec C, changer le nom du compilateur de **vbc** à **csc,** et changer l’extension du fichier de .vb à .cs:

```console
csc example.cs /r:UtilityLib.dll
```

## <a name="see-also"></a>Voir aussi

- <xref:System.CLSCompliantAttribute>
