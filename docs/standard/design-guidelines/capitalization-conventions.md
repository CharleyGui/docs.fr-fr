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
ms.openlocfilehash: 10d628700a9cbf0e842416878ec2c7febfa3d6f5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280398"
---
# <a name="capitalization-conventions"></a>Conventions de mise en majuscules
Les instructions de ce chapitre présentent une méthode simple pour l’utilisation de cas qui, lorsqu’elle est appliquée de manière cohérente, facilite la lecture des identificateurs des types, des membres et des paramètres.

## <a name="capitalization-rules-for-identifiers"></a>Règles de mise en majuscules pour les identificateurs
 Pour différencier les mots dans un identificateur, mettez en majuscule la première lettre de chaque mot dans l’identificateur. N’utilisez pas de traits de soulignement pour différencier des mots, ou à cette question, n’importe où dans les identificateurs. Il existe deux façons de mettre des identificateurs en majuscules, en fonction de l’utilisation de l’identificateur :

- PascalCasing

- camelCasing

 La Convention PascalCasing, utilisée pour tous les identificateurs à l’exception des noms de paramètres, met en majuscule le premier caractère de chaque mot (y compris les acronymes de longueur de deux lettres), comme indiqué dans les exemples suivants :

 `PropertyDescriptor`
 `HtmlTag`

 Un cas spécial est fait pour les acronymes à deux lettres dans lesquels les deux lettres sont en majuscules, comme indiqué dans l’identificateur suivant :

 `IOStream`

 La Convention camelCasing, utilisée uniquement pour les noms de paramètres, met en majuscule le premier caractère de chaque mot, à l’exception du premier mot, comme indiqué dans les exemples suivants. Comme l’illustre l’exemple, les acronymes à deux lettres qui commencent un identificateur en casse mixte sont à la fois en minuscules.

 `propertyDescriptor`
 `ioStream`
 `htmlTag`

 ✔️ Utilisez PascalCasing pour tous les noms de membre, de type et d’espace de noms publics composés de plusieurs mots.

 ✔️ Utilisez camelCasing pour les noms de paramètres.

 Le tableau suivant décrit les règles de mise en majuscules pour les différents types d’identificateurs.

|Identificateur|Casse|Exemple|
|----------------|------------|-------------|
|Espace de noms|Casse|`namespace System.Security { ... }`|
|Type|Casse|`public class StreamReader { ... }`|
|Interface|Casse|`public interface IEnumerable { ... }`|
|Méthode|Casse|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|
|Propriété|Casse|`public class String {` <br />  `public int Length { get; }` <br /> `}`|
|Événement|Casse|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|
|Champ|Casse|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|
|Valeur enum|Casse|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|
|Paramètre|mixte|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|

## <a name="capitalizing-compound-words-and-common-terms"></a>Mettre en majuscules les mots composés et les termes courants
 La plupart des termes composés sont traités comme des mots simples à des fins de mise en majuscules.

 ❌NE pas mettre en majuscules chaque mot dans les mots composés « fermés ».

 Il s’agit de mots composés écrits sous la forme d’un mot unique, tel qu’un point de terminaison. Dans le cadre des instructions de la casse, traitez un mot composé fermé comme un mot unique. Utilisez un dictionnaire actuel pour déterminer si un mot composé est écrit sous forme fermée.

|Casse|mixte|Not|
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
 Les langages qui peuvent s’exécuter sur le CLR ne sont pas requis pour prendre en charge le respect de la casse, bien que d’autres. Même si votre langage le prend en charge, les autres langages qui peuvent accéder à votre infrastructure ne le sont pas. Par conséquent, toutes les API qui sont accessibles de l’extérieur ne peuvent pas s’appuyer uniquement sur la casse pour faire la distinction entre deux noms dans le même contexte.

 ❌NE partez pas du principe que tous les langages de programmation respectent la casse. mais ils ne le sont pas. Les noms ne peuvent pas différer uniquement par la casse.

 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*

 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*

## <a name="see-also"></a>Voir aussi

- [Directives de conception d’infrastructure](index.md)
- [Instructions d’affectation de noms](naming-guidelines.md)
