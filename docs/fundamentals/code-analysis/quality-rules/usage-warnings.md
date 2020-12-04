---
title: Règles d’utilisation (analyse du code)
description: En savoir plus sur les règles d’utilisation de l’analyse du code.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.usagerules
helpviewer_keywords:
- rules, usage
- managed code analysis rules, usage rules
- usage rules
author: gewarren
ms.author: gewarren
ms.openlocfilehash: c8b14d2f92502d5a82e41a322e599745bdcf8b85
ms.sourcegitcommit: a6bd4cad438fe479cbd112eae10f2cd449f06e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2020
ms.locfileid: "96588083"
---
# <a name="usage-rules"></a>Règles d’utilisation

Les règles d’utilisation prennent en charge l’utilisation correcte de .NET.

## <a name="in-this-section"></a>Dans cette section

|Règle|Description|
|----------|-----------------|
|[CA1801 : Passez en revue les paramètres inutilisés](ca1801.md)|Une signature de méthode inclut un paramètre qui n'est pas utilisé dans le corps de la méthode.|
|[CA1816 : Appeler GC.SuppressFinalize correctement](ca1816.md)|Une méthode qui est une implémentation de dispose n’appelle pas `GC.SuppressFinalize` ; ou une méthode qui n’est pas une implémentation d' `Dispose` appels `GC.SuppressFinalize` ; ou une méthode appelle `GC.SuppressFinalize` et passe autre chose que `this` ( `Me` en Visual Basic).|
|[CA2200 : Levez à nouveau une exception pour conserver les détails de la pile](ca2200.md)|Une exception est à nouveau levée et est spécifiée explicitement dans l'instruction throw. Si une exception est à nouveau levée par sa spécification dans l'instruction throw, la liste des appels de méthode présents entre la méthode d'origine qui a levé l'exception et la méthode actuelle est perdue.|
|[CA2201 : Ne levez pas des types d'exceptions réservés](ca2201.md)|Cela rend l’erreur d’origine difficile à détecter et à déboguer.|
|[CA2207 : Initialisez les champs statiques des types valeur en ligne](ca2207.md)|Un type valeur déclare un constructeur statique explicite. Pour corriger une violation de cette règle, initialisez toutes les données statiques lorsqu’elles sont déclarées et supprimez le constructeur statique.|
|[CA2208 : Instanciez les exceptions d'argument comme il se doit](ca2208.md)|Un appel est passé au constructeur par défaut (sans paramètre) d'un type d'exception qui est ou dérive d'ArgumentException, ou un argument string incorrect est passé à un constructeur paramétrable d'un type d'exception qui est ou dérive d'ArgumentException.|
|[CA2211 : Les champs non constants ne doivent pas être visibles](ca2211.md)|Les champs statiques qui ne sont pas des constantes ou en lecture seule ne sont pas thread-safe. L’accès à ce champ doit être contrôlé avec soin et nécessite des techniques de programmation avancées pour la synchronisation de l’accès à l’objet de classe.|
|[CA2213 : Les champs pouvant être supprimés doivent l’être](ca2213.md)|Un type qui implémente <xref:System.IDisposable?displayProperty=fullName> déclare des champs de types qui implémentent également `IDisposable` . La `Dispose` méthode du champ n’est pas appelée par la `Dispose` méthode du type déclarant.|
|[CA2214 : N'appelez pas de méthodes substituables dans les constructeurs](ca2214.md)|Quand un constructeur appelle une méthode virtuelle, il est possible que le constructeur de l’instance qui appelle la méthode n’ait pas été exécuté.|
|[CA2215 : Les méthodes Dispose doivent appeler la méthode Dispose de la classe de base](ca2215.md)|Si un type hérite d’un type supprimable, il doit appeler la `Dispose` méthode du type de base à partir de sa propre `Dispose` méthode.|
|[CA2216 : Les types pouvant être supprimés doivent déclarer un finaliseur](ca2216.md)|Un type qui implémente <xref:System.IDisposable?displayProperty=fullName> et a des champs qui suggèrent l’utilisation de ressources non managées, n’implémente pas de finaliseur comme décrit par `Object.Finalize` .|
|[CA2217 : Ne marquez pas les enums avec l'attribut FlagsAttribute](ca2217.md)|Une énumération visible de l’extérieur est marquée avec `FlagsAttribute` , et elle a une ou plusieurs valeurs qui ne sont pas des puissances de deux ou une combinaison des autres valeurs définies sur l’énumération.|
|[CA2218 : Remplacez GetHashCode au moment de remplacer Equals](ca2218.md)|Un type public substitue <xref:System.Object.Equals%2A?displayProperty=fullName> mais ne remplace pas <xref:System.Object.GetHashCode%2A?displayProperty=fullName> .|
|[CA2219 : Ne pas lever d'exceptions dans les clauses d'exception](ca2219.md)|Lorsqu'une exception est levée dans une clause finally ou fault, la nouvelle exception masque l'exception active. Lorsqu'une exception est levée dans une clause filter, le runtime l'intercepte en silence. Cela rend l’erreur d’origine difficile à détecter et à déboguer.|
|[CA2224 : Remplacez Equals au moment de surcharger l'opérateur égal](ca2224.md)|Un type public implémente l’opérateur d’égalité, mais ne remplace pas <xref:System.Object.Equals%2A?displayProperty=fullName> .|
|[CA2225 : Les surcharges d'opérateur offrent d'autres méthodes nommées](ca2225.md)|Une surcharge d'opérateur a été détectée, et la méthode de substitution nommée attendue n'a pas été trouvée. Le membre de substitution nommé fournit l’accès aux mêmes fonctionnalités que l’opérateur et est fourni aux développeurs qui programment dans des langages qui ne prennent pas en charge les opérateurs surchargés.|
|[CA2226 : Les opérateurs doivent contenir des surcharges symétriques](ca2226.md)|Un type implémente l’opérateur d’égalité ou d’inégalité et n’implémente pas l’opérateur opposé.|
|[CA2227 : Les propriétés de collection doivent être en lecture seule](ca2227.md)|Une propriété de collection accessible en écriture permet à un utilisateur de remplacer la collection par une collection différente. Une propriété en lecture seule empêche le remplacement de la collection, mais permet quand même aux membres individuels d’être définis.|
|[CA2229 : Implémentez des constructeurs de sérialisation](ca2229.md)|Pour corriger une violation de cette règle, implémentez le constructeur de sérialisation. Dans le cas d'une classe sealed, rendez le constructeur privé ; sinon, attribuez-lui l'état protégé.|
|[CA2231 : Surchargez l’opérateur égal (equals) en remplaçant ValueType.Equals](ca2231.md)|Un type valeur se substitue à `Object.Equals` , mais n’implémente pas l’opérateur d’égalité.|
|[CA2234 : Passez des objets System.Uri à la place de chaînes](ca2234.md)|Un appel est passé à une méthode qui a un paramètre de chaîne dont le nom contient « uri », « URI », « urn », « URN », « url » ou « URL ».  Le type déclarant de la méthode contient une surcharge de méthode correspondante qui a un <xref:System.Uri?displayProperty=fullName> paramètre.|
|[CA2235 : Marquez tous les champs non sérialisés](ca2235.md)|Un champ d'instance d'un type non sérialisable est déclaré dans un type sérialisable.|
|[CA2237 : Marquer les types ISerializable avec SerializableAttribute](ca2237.md)|Pour être reconnus par le common language runtime comme sérialisables, les types doivent être marqués avec l’attribut SerializableAttribute même si le type utilise une routine de sérialisation personnalisée par le biais de l’implémentation de l' `ISerializable` interface.|
|[CA2241 : Indiquer le nombre correct d'arguments dans les méthodes de mise en forme](ca2241.md)|L’argument de format passé à <xref:System.String.Format%2A?displayProperty=nameWithType> ne contient pas d’élément de mise en forme qui correspond à chaque argument d’objet, ou vice versa.|
|[CA2242 : Effectuez correctement des tests NaN](ca2242.md)|Cette expression teste une valeur par rapport à `Single.Nan` ou `Double.Nan` . Utilisez `Single.IsNan(Single)` ou `Double.IsNan(Double)` pour tester la valeur.|
|[CA2243 : Les littéraux de chaîne d'attribut doivent être analysés correctement](ca2243.md)|Le paramètre de littéral de chaîne d’un attribut n’est pas analysé correctement pour une URL, un GUID ou une version.|
|[CA2244 : Ne pas dupliquer les initialisations d’éléments indexés](ca2244.md)|Un initialiseur d’objet a plus d’un initialiseur d’élément indexé avec le même index constant. Tout sauf le dernier initialiseur est redondant.|
|[CA2245 : Ne pas attribuer une propriété à elle-même](ca2245.md)|Une propriété a été accidentellement assignée à elle-même.|
|[CA2246 : Ne pas attribuer un symbole et son membre dans la même instruction](ca2246.md)|L’assignation d’un symbole et de son membre, autrement dit, un champ ou une propriété, dans la même instruction n’est pas recommandée. Il n’est pas évident de préciser si l’accès au membre était destiné à utiliser l’ancienne valeur du symbole avant l’assignation ou la nouvelle valeur de l’assignation dans cette instruction.|
|[CA2247 : L’argument passé au constructeur TaskCompletionSource doit être l’enum TaskCreationOptions au lieu de l’enum TaskContinuationOptions](ca2246.md)|TaskCompletionSource possède des constructeurs qui prennent des TaskCreationOptions qui contrôlent la tâche sous-jacente, et les constructeurs qui prennent l’état d’objet stocké dans la tâche.  Le passage accidentel d’un TaskContinuationOptions au lieu d’un TaskCreationOptions entraînera l’appel du traitement des options en tant qu’État.|
|[CA2248 : fournissez un argument « enum » correct à « Enum. HasFlag »](ca2248.md)|Le type enum passé comme argument à l' `HasFlag` appel de méthode est différent du type enum appelant.|
|[CA2249 : Utiliser de préférence String.Contains à la place de String.IndexOf](ca2249.md)|Les appels à `string.IndexOf` où le résultat est utilisé pour vérifier la présence ou l’absence d’une sous-chaîne peuvent être remplacés par `string.Contains` .|
