---
title: Conventions de mise en majuscules
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
ms.openlocfilehash: 8af4a15e1e5b34c38b14c6b547cf44801bbf13e6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741758"
---
# <a name="capitalization-conventions"></a>Conventions de mise en majuscules
Les lignes directrices de ce chapitre présentent une méthode simple d'utilisation des cas qui, lorsqu'ils sont appliqués de façon uniforme, rendent les identificateurs pour les types, les membres et les paramètres faciles à lire.

## <a name="capitalization-rules-for-identifiers"></a>Règles de mise en majuscules pour les identificateurs
 Afin de distinguer les mots dans un identificateur, il faut y mettre en majuscule la première lettre de chaque mot. N’utilisez pas de traits de soulignement pour différencier des mots, ni ailleurs à cette fin dans les identificateurs. Il existe deux façons appropriées d’utiliser des majuscules pour les identificateurs, en fonction de son utilisation :

- PascalCasing

- casseCamel

 La convention CassePascal, utilisée pour tous les identificateurs à l’exception des noms de paramètres, met en majuscule le premier caractère de chaque mot (y compris les acronymes d’une longueur de deux lettres), comme indiqué dans les exemples suivants :

 `PropertyDescriptor`
 `HtmlTag`

 Un cas spécial est fait pour les acronymes à deux lettres dans lesquels les deux lettres sont en majuscules, comme indiqué dans l’identificateur suivant :

 `IOStream`

 La convention casseCamel, utilisée uniquement pour les noms de paramètres, met en majuscule le premier caractère de chaque mot, sauf le premier mot, comme indiqué dans les exemples suivants. Comme le montre également l’exemple, les acronymes de deux lettres qui sont au début d’un identificateur à casse mixte sont tout en minuscules.

 `propertyDescriptor`
 `ioStream`
 `htmlTag`

 ✔️ Utilisez PascalCasing pour tous les noms de membre, de type et d’espace de noms publics composés de plusieurs mots.

 ✔️ Utilisez camelCasing pour les noms de paramètres.

 Le tableau suivant décrit les règles de mise en majuscules pour les différents types d’identificateurs.

|Identificateur|Casse|Exemple|
|----------------|------------|-------------|
|Espace de noms|Pascal|`namespace System.Security { ... }`|
|Type|Pascal|`public class StreamReader { ... }`|
|Interface|Pascal|`public interface IEnumerable { ... }`|
|Méthode|Pascal|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|
|Propriété|Pascal|`public class String {` <br />  `public int Length { get; }` <br /> `}`|
|Événement|Pascal|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|
|Champ|Pascal|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|
|Valeur enum|Pascal|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|
|Paramètre|mixte|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|

## <a name="capitalizing-compound-words-and-common-terms"></a>Mettre en majuscules les mots composés et les termes courants
 La plupart des termes composés sont traités comme des mots simples à des fins de mise en majuscules.

 ❌ ne pas mettre en majuscules chaque mot dans les mots composés « fermés ».

 Il s’agit de mots composés écrits sous la forme d’un mot unique, tel qu’un point de terminaison. Dans le cadre des instructions de la casse, traitez un mot composé fermé comme un mot unique. Utilisez un dictionnaire actuel pour déterminer si un mot composé est écrit sous forme fermée.

|Pascal|mixte|not|
|------------|-----------|---------|
|`BitFlag`|`bitFlag`|`Bitflag`|
|`Callback`|`callback`|`CallBack`|
|`Canceled`|`canceled`|`Cancelled`|
|`DoNot`|`doNot`|`Don't`|
|`Email`|`email`|`EMail`|
|`Endpoint`|`endpoint`|`EndPoint`|
|`FileName`|`fileName`|`Filename`|
|`Gridline`|`gridline`|`GridLine`|
|`Hashtable`|`hashtable`|`HashTable`|
|`Id`|`id`|`ID`|
|`Indexes`|`indexes`|`Indices`|
|`LogOff`|`logOff`|`LogOut`|
|`LogOn`|`logOn`|`LogIn`|
|`Metadata`|`metadata`|`MetaData, metaData`|
|`Multipanel`|`multipanel`|`MultiPanel`|
|`Multiview`|`multiview`|`MultiView`|
|`Namespace`|`namespace`|`NameSpace`|
|`Ok`|`ok`|`OK`|
|`Pi`|`pi`|`PI`|
|`Placeholder`|`placeholder`|`PlaceHolder`|
|`SignIn`|`signIn`|`SignOn`|
|`SignOut`|`signOut`|`SignOff`|
|`UserName`|`userName`|`Username`|
|`WhiteSpace`|`whiteSpace`|`Whitespace`|
|`Writable`|`writable`|`Writeable`|

## <a name="case-sensitivity"></a>Respect de la casse
 Les langages qui peuvent s’exécuter sur le CLR n’ont pas l’obligation de prendre en charge le respect de la casse, bien que certains le fassent. Même si votre langage le prend en charge, d'autres langages qui pourraient accéder à votre framework ne le font pas. Les API qui sont accessibles de l'extérieur ne peuvent donc pas se fier uniquement à la casse pour distinguer deux noms dans le même contexte.

 ❌ ne supposez pas que tous les langages de programmation respectent la casse. mais ils ne le sont pas. Les noms ne peuvent pas différer seulement par la casse.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
- [Directives de nommage](../../../docs/standard/design-guidelines/naming-guidelines.md)
