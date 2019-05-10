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
author: KrzysztofCwalina
ms.openlocfilehash: e0da4cd747846921d170d9c07d6f1fb91dbd4ed7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615250"
---
# <a name="capitalization-conventions"></a>Conventions de mise en majuscules
Les lignes directrices de ce chapitre présentent une méthode simple d'utilisation des cas qui, lorsqu'ils sont appliqués de façon uniforme, rendent les identificateurs pour les types, les membres et les paramètres faciles à lire.  
  
## <a name="capitalization-rules-for-identifiers"></a>Règles de casse des identificateurs  
 Afin de distinguer les mots dans un identificateur, il faut y mettre en majuscule la première lettre de chaque mot. N’utilisez pas de traits de soulignement pour différencier des mots, ni ailleurs à cette fin dans les identificateurs. Il existe deux façons appropriées d’utiliser des majuscules pour les identificateurs, en fonction de son utilisation :  
  
- PascalCasing  
  
- casseCamel  
  
 La convention CassePascal, utilisée pour tous les identificateurs à l’exception des noms de paramètres, met en majuscule le premier caractère de chaque mot (y compris les acronymes d’une longueur de deux lettres), comme indiqué dans les exemples suivants :  
  
 `PropertyDescriptor`  
 `HtmlTag`  
  
 Un cas particulier concerne des acronymes de deux lettres dans lequel les deux lettres sont en majuscules, comme indiqué dans l’identificateur suivant :  
  
 `IOStream`  
  
 La convention casseCamel, utilisée uniquement pour les noms de paramètres, met en majuscule le premier caractère de chaque mot, sauf le premier mot, comme indiqué dans les exemples suivants. Comme le montre également l’exemple, les acronymes de deux lettres qui sont au début d’un identificateur à casse mixte sont tout en minuscules.  
  
 `propertyDescriptor`  
 `ioStream`  
 `htmlTag`  
  
 **✓ UTILISEZ** la convention CassePascal pour tous les noms de membres, de types et d’espaces de noms publics constitué de plusieurs mots.  
  
 **✓ UTILISEZ** la convention casseCamel pour les noms de paramètre.  
  
 Le tableau suivant décrit les règles de mise en majuscules pour différents types d’identificateurs.  
  
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
|Paramètre|Camel|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|  
  
## <a name="capitalizing-compound-words-and-common-terms"></a>Tirant partis de la casse des mots composés et les termes courants  
 La plupart des termes composés sont considérés comme des termes uniques à des fins de mise en majuscules.  
  
 **X N’UTILISEZ PAS DE MAJUSCULE** au début de chaque mot dans les mots composés dits fermés.  
  
 Il s’agit des mots composés écrites sous la forme d’un mot unique, comme point de terminaison. Pour les besoins de recommandations de la casse, traiter un fermeture mot composé comme un mot unique. Utiliser un dictionnaire en cours pour déterminer si un mot composé est écrit dans une forme fermée.  
  
|Pascal|Camel|Ne convient pas|  
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
  
 **X NE SUPPOSEZ PAS** que tous les langages de programmation respectent la casse. Ce n’est pas le cas. Les noms ne peuvent pas différer seulement par la casse.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [instructions de conception Framework : Conventions, les idiomes et les modèles pour les bibliothèques .NET réutilisable, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi

- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
- [Directives de nommage](../../../docs/standard/design-guidelines/naming-guidelines.md)
