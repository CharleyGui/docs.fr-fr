---
title: Conventions de mise en majuscules
description: Appliquer des conventions de mise en majuscules pour les identificateurs, les mots composés et les termes courants. Comprendre le fonctionnement du respect de la casse dans .NET.
ms.date: 10/22/2008
helpviewer_keywords:
- camel-case names [.NET Framework]
- class library design guidelines [.NET Framework], capitalization
- Pascal-case names [.NET Framework]
- case sensitivity, capitalization conventions
- names [.NET Framework], capitalization
ms.assetid: 4c4ea526-9203-486f-b72d-29d61c5b3c6d
ms.openlocfilehash: e416a8346952a41d9c89f526bfce990dfc277fc1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701261"
---
# <a name="capitalization-conventions"></a><span data-ttu-id="e33b3-104">Conventions de mise en majuscules</span><span class="sxs-lookup"><span data-stu-id="e33b3-104">Capitalization Conventions</span></span>

<span data-ttu-id="e33b3-105">Les instructions de ce chapitre présentent une méthode simple pour l’utilisation de cas qui, lorsqu’elle est appliquée de manière cohérente, facilite la lecture des identificateurs des types, des membres et des paramètres.</span><span class="sxs-lookup"><span data-stu-id="e33b3-105">The guidelines in this chapter lay out a simple method for using case that, when applied consistently, make identifiers for types, members, and parameters easy to read.</span></span>

## <a name="capitalization-rules-for-identifiers"></a><span data-ttu-id="e33b3-106">Règles de mise en majuscules pour les identificateurs</span><span class="sxs-lookup"><span data-stu-id="e33b3-106">Capitalization Rules for Identifiers</span></span>

 <span data-ttu-id="e33b3-107">Pour différencier les mots dans un identificateur, mettez en majuscule la première lettre de chaque mot dans l’identificateur.</span><span class="sxs-lookup"><span data-stu-id="e33b3-107">To differentiate words in an identifier, capitalize the first letter of each word in the identifier.</span></span> <span data-ttu-id="e33b3-108">N’utilisez pas de traits de soulignement pour différencier des mots, ou à cette question, n’importe où dans les identificateurs.</span><span class="sxs-lookup"><span data-stu-id="e33b3-108">Do not use underscores to differentiate words, or for that matter, anywhere in identifiers.</span></span> <span data-ttu-id="e33b3-109">Il existe deux façons de mettre des identificateurs en majuscules, en fonction de l’utilisation de l’identificateur :</span><span class="sxs-lookup"><span data-stu-id="e33b3-109">There are two appropriate ways to capitalize identifiers, depending on the use of the identifier:</span></span>

- <span data-ttu-id="e33b3-110">PascalCasing</span><span class="sxs-lookup"><span data-stu-id="e33b3-110">PascalCasing</span></span>

- <span data-ttu-id="e33b3-111">camelCasing</span><span class="sxs-lookup"><span data-stu-id="e33b3-111">camelCasing</span></span>

 <span data-ttu-id="e33b3-112">La Convention PascalCasing, utilisée pour tous les identificateurs à l’exception des noms de paramètres, met en majuscule le premier caractère de chaque mot (y compris les acronymes de longueur de deux lettres), comme indiqué dans les exemples suivants :</span><span class="sxs-lookup"><span data-stu-id="e33b3-112">The PascalCasing convention, used for all identifiers except parameter names, capitalizes the first character of each word (including acronyms over two letters in length), as shown in the following examples:</span></span>

 `PropertyDescriptor`
 `HtmlTag`

 <span data-ttu-id="e33b3-113">Un cas spécial est fait pour les acronymes à deux lettres dans lesquels les deux lettres sont en majuscules, comme indiqué dans l’identificateur suivant :</span><span class="sxs-lookup"><span data-stu-id="e33b3-113">A special case is made for two-letter acronyms in which both letters are capitalized, as shown in the following identifier:</span></span>

 `IOStream`

 <span data-ttu-id="e33b3-114">La Convention camelCasing, utilisée uniquement pour les noms de paramètres, met en majuscule le premier caractère de chaque mot, à l’exception du premier mot, comme indiqué dans les exemples suivants.</span><span class="sxs-lookup"><span data-stu-id="e33b3-114">The camelCasing convention, used only for parameter names, capitalizes the first character of each word except the first word, as shown in the following examples.</span></span> <span data-ttu-id="e33b3-115">Comme l’illustre l’exemple, les acronymes à deux lettres qui commencent un identificateur en casse mixte sont à la fois en minuscules.</span><span class="sxs-lookup"><span data-stu-id="e33b3-115">As the example also shows, two-letter acronyms that begin a camel-cased identifier are both lowercase.</span></span>

 `propertyDescriptor`
 `ioStream`
 `htmlTag`

 <span data-ttu-id="e33b3-116">✔️ Utilisez PascalCasing pour tous les noms de membre, de type et d’espace de noms publics composés de plusieurs mots.</span><span class="sxs-lookup"><span data-stu-id="e33b3-116">✔️ DO use PascalCasing for all public member, type, and namespace names consisting of multiple words.</span></span>

 <span data-ttu-id="e33b3-117">✔️ Utilisez camelCasing pour les noms de paramètres.</span><span class="sxs-lookup"><span data-stu-id="e33b3-117">✔️ DO use camelCasing for parameter names.</span></span>

 <span data-ttu-id="e33b3-118">Le tableau suivant décrit les règles de mise en majuscules pour les différents types d’identificateurs.</span><span class="sxs-lookup"><span data-stu-id="e33b3-118">The following table describes the capitalization rules for different types of identifiers.</span></span>

|<span data-ttu-id="e33b3-119">Identificateur</span><span class="sxs-lookup"><span data-stu-id="e33b3-119">Identifier</span></span>|<span data-ttu-id="e33b3-120">Casse</span><span class="sxs-lookup"><span data-stu-id="e33b3-120">Casing</span></span>|<span data-ttu-id="e33b3-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="e33b3-121">Example</span></span>|
|----------------|------------|-------------|
|<span data-ttu-id="e33b3-122">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="e33b3-122">Namespace</span></span>|<span data-ttu-id="e33b3-123">Casse</span><span class="sxs-lookup"><span data-stu-id="e33b3-123">Pascal</span></span>|`namespace System.Security { ... }`|
|<span data-ttu-id="e33b3-124">Type</span><span class="sxs-lookup"><span data-stu-id="e33b3-124">Type</span></span>|<span data-ttu-id="e33b3-125">Casse</span><span class="sxs-lookup"><span data-stu-id="e33b3-125">Pascal</span></span>|`public class StreamReader { ... }`|
|<span data-ttu-id="e33b3-126">Interface</span><span class="sxs-lookup"><span data-stu-id="e33b3-126">Interface</span></span>|<span data-ttu-id="e33b3-127">Casse</span><span class="sxs-lookup"><span data-stu-id="e33b3-127">Pascal</span></span>|`public interface IEnumerable { ... }`|
|<span data-ttu-id="e33b3-128">Méthode</span><span class="sxs-lookup"><span data-stu-id="e33b3-128">Method</span></span>|<span data-ttu-id="e33b3-129">Casse</span><span class="sxs-lookup"><span data-stu-id="e33b3-129">Pascal</span></span>|`public class Object {` <br />  `public virtual string ToString();` <br /> `}`|
|<span data-ttu-id="e33b3-130">Propriété</span><span class="sxs-lookup"><span data-stu-id="e33b3-130">Property</span></span>|<span data-ttu-id="e33b3-131">Casse</span><span class="sxs-lookup"><span data-stu-id="e33b3-131">Pascal</span></span>|`public class String {` <br />  `public int Length { get; }` <br /> `}`|
|<span data-ttu-id="e33b3-132">Événement</span><span class="sxs-lookup"><span data-stu-id="e33b3-132">Event</span></span>|<span data-ttu-id="e33b3-133">Casse</span><span class="sxs-lookup"><span data-stu-id="e33b3-133">Pascal</span></span>|`public class Process {` <br />  `public event EventHandler Exited;` <br /> `}`|
|<span data-ttu-id="e33b3-134">Champ</span><span class="sxs-lookup"><span data-stu-id="e33b3-134">Field</span></span>|<span data-ttu-id="e33b3-135">Casse</span><span class="sxs-lookup"><span data-stu-id="e33b3-135">Pascal</span></span>|`public class MessageQueue {` <br />  `public static readonly TimeSpan` <br /> `InfiniteTimeout;` <br /> `}` <br /> `public struct UInt32 {` <br />  `public const Min = 0;` <br /> `}`|
|<span data-ttu-id="e33b3-136">Valeur enum</span><span class="sxs-lookup"><span data-stu-id="e33b3-136">Enum value</span></span>|<span data-ttu-id="e33b3-137">Casse</span><span class="sxs-lookup"><span data-stu-id="e33b3-137">Pascal</span></span>|`public enum FileMode {` <br />  `Append,` <br />  `...` <br /> `}`|
|<span data-ttu-id="e33b3-138">Paramètre</span><span class="sxs-lookup"><span data-stu-id="e33b3-138">Parameter</span></span>|<span data-ttu-id="e33b3-139">mixte</span><span class="sxs-lookup"><span data-stu-id="e33b3-139">Camel</span></span>|`public class Convert {` <br />  `public static int ToInt32(string value);` <br /> `}`|

## <a name="capitalizing-compound-words-and-common-terms"></a><span data-ttu-id="e33b3-140">Mettre en majuscules les mots composés et les termes courants</span><span class="sxs-lookup"><span data-stu-id="e33b3-140">Capitalizing Compound Words and Common Terms</span></span>

 <span data-ttu-id="e33b3-141">La plupart des termes composés sont traités comme des mots simples à des fins de mise en majuscules.</span><span class="sxs-lookup"><span data-stu-id="e33b3-141">Most compound terms are treated as single words for purposes of capitalization.</span></span>

 <span data-ttu-id="e33b3-142">❌ NE pas mettre en majuscules chaque mot dans les mots composés « fermés ».</span><span class="sxs-lookup"><span data-stu-id="e33b3-142">❌ DO NOT capitalize each word in so-called closed-form compound words.</span></span>

 <span data-ttu-id="e33b3-143">Il s’agit de mots composés écrits sous la forme d’un mot unique, tel qu’un point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="e33b3-143">These are compound words written as a single word, such as endpoint.</span></span> <span data-ttu-id="e33b3-144">Dans le cadre des instructions de la casse, traitez un mot composé fermé comme un mot unique.</span><span class="sxs-lookup"><span data-stu-id="e33b3-144">For the purpose of casing guidelines, treat a closed-form compound word as a single word.</span></span> <span data-ttu-id="e33b3-145">Utilisez un dictionnaire actuel pour déterminer si un mot composé est écrit sous forme fermée.</span><span class="sxs-lookup"><span data-stu-id="e33b3-145">Use a current dictionary to determine if a compound word is written in closed form.</span></span>

|<span data-ttu-id="e33b3-146">Casse</span><span class="sxs-lookup"><span data-stu-id="e33b3-146">Pascal</span></span>|<span data-ttu-id="e33b3-147">mixte</span><span class="sxs-lookup"><span data-stu-id="e33b3-147">Camel</span></span>|<span data-ttu-id="e33b3-148">not</span><span class="sxs-lookup"><span data-stu-id="e33b3-148">Not</span></span>|
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

## <a name="case-sensitivity"></a><span data-ttu-id="e33b3-149">Respect de la casse</span><span class="sxs-lookup"><span data-stu-id="e33b3-149">Case Sensitivity</span></span>

 <span data-ttu-id="e33b3-150">Les langages qui peuvent s’exécuter sur le CLR ne sont pas requis pour prendre en charge le respect de la casse, bien que d’autres.</span><span class="sxs-lookup"><span data-stu-id="e33b3-150">Languages that can run on the CLR are not required to support case-sensitivity, although some do.</span></span> <span data-ttu-id="e33b3-151">Même si votre langage le prend en charge, les autres langages qui peuvent accéder à votre infrastructure ne le sont pas.</span><span class="sxs-lookup"><span data-stu-id="e33b3-151">Even if your language supports it, other languages that might access your framework do not.</span></span> <span data-ttu-id="e33b3-152">Par conséquent, toutes les API qui sont accessibles de l’extérieur ne peuvent pas s’appuyer uniquement sur la casse pour faire la distinction entre deux noms dans le même contexte.</span><span class="sxs-lookup"><span data-stu-id="e33b3-152">Any APIs that are externally accessible, therefore, cannot rely on case alone to distinguish between two names in the same context.</span></span>

 <span data-ttu-id="e33b3-153">❌ NE partez pas du principe que tous les langages de programmation respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="e33b3-153">❌ DO NOT assume that all programming languages are case sensitive.</span></span> <span data-ttu-id="e33b3-154">mais ils ne le sont pas.</span><span class="sxs-lookup"><span data-stu-id="e33b3-154">They are not.</span></span> <span data-ttu-id="e33b3-155">Les noms ne peuvent pas différer uniquement par la casse.</span><span class="sxs-lookup"><span data-stu-id="e33b3-155">Names cannot differ by case alone.</span></span>

 <span data-ttu-id="e33b3-156">*Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*</span><span class="sxs-lookup"><span data-stu-id="e33b3-156">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="e33b3-157">*Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="e33b3-157">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="e33b3-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e33b3-158">See also</span></span>

- [<span data-ttu-id="e33b3-159">Directives de conception d’infrastructure</span><span class="sxs-lookup"><span data-stu-id="e33b3-159">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="e33b3-160">Instructions d’affectation de noms</span><span class="sxs-lookup"><span data-stu-id="e33b3-160">Naming Guidelines</span></span>](naming-guidelines.md)
