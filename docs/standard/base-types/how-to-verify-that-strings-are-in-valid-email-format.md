---
title: Guide pratique pour vérifier que des chaînes sont dans un format d’adresse e-mail valide
description: Lire un exemple de la façon dont une expression régulière vérifie que les chaînes sont dans un format d’adresse de messagerie valide dans .NET.
ms.date: 06/30/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- user input, examples
- Regex.IsMatch method
- regular expressions [.NET], examples
- examples [Visual Basic], strings
- IsValidEmail
- validation, email strings
- input, checking
- strings [.NET], examples [Visual Basic]
- email [.NET], validating
- IsMatch method
ms.assetid: 7536af08-4e86-4953-98a1-a8298623df92
ms.openlocfilehash: 88ff326e16ede6a422e9403b71905845014c4c25
ms.sourcegitcommit: 6d1ae17e60384f3b5953ca7b45ac859ec6d4c3a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94982490"
---
# <a name="how-to-verify-that-strings-are-in-valid-email-format"></a><span data-ttu-id="dd552-103">Guide pratique pour vérifier que des chaînes sont dans un format d’adresse e-mail valide</span><span class="sxs-lookup"><span data-stu-id="dd552-103">How to verify that strings are in valid email format</span></span>

<span data-ttu-id="dd552-104">L'exemple suivant utilise une expression régulière pour vérifier qu'une chaîne est dans un format d'adresse e-mail valide.</span><span class="sxs-lookup"><span data-stu-id="dd552-104">The following example uses a regular expression to verify that a string is in valid email format.</span></span>

<span data-ttu-id="dd552-105">Cette expression régulière est relativement simple à ce qui peut être utilisé en tant qu’e-mail.</span><span class="sxs-lookup"><span data-stu-id="dd552-105">This regular expression is comparatively simple to what can actually be used as an email.</span></span> <span data-ttu-id="dd552-106">L’utilisation d’une expression régulière pour valider un message électronique est utile pour s’assurer que la structure d’un message électronique est correcte, mais il ne s’agit pas d’une substitution pour vérifier que le courrier électronique existe réellement.</span><span class="sxs-lookup"><span data-stu-id="dd552-106">Using a regular expression to validate an email is useful to make sure the structure of an email is correct, but it isn't a substitution for verifying the email actually exists.</span></span>

<span data-ttu-id="dd552-107">✔️ Utilisez une petite expression régulière pour vérifier la structure valide d’un e-mail.</span><span class="sxs-lookup"><span data-stu-id="dd552-107">✔️ DO use a small regular expression to check for the valid structure of an email.</span></span>

<span data-ttu-id="dd552-108">✔️ Envoyer un message électronique de test à l’adresse fournie par un utilisateur de votre application.</span><span class="sxs-lookup"><span data-stu-id="dd552-108">✔️ DO send a test email to the address provided by a user of your app.</span></span>

<span data-ttu-id="dd552-109">❌ N’utilisez pas une expression régulière comme seule façon de valider un e-mail.</span><span class="sxs-lookup"><span data-stu-id="dd552-109">❌ DON'T use a regular expression as the only way you validate an email.</span></span>

<span data-ttu-id="dd552-110">Si vous essayez de créer l’expression régulière _parfaite_ pour valider que la structure d’un message électronique est correcte, l’expression devient tellement complexe qu’il est incroyablement difficile de déboguer ou d’améliorer.</span><span class="sxs-lookup"><span data-stu-id="dd552-110">If you try to create the _perfect_ regular expression to validate that the structure of an email is correct, the expression becomes so complex that it's incredibly difficult to debug or improve.</span></span> <span data-ttu-id="dd552-111">Les expressions régulières ne peuvent pas valider l’existence d’un courrier électronique, même s’il est correctement structuré.</span><span class="sxs-lookup"><span data-stu-id="dd552-111">Regular expressions can't validate an email exists, even if it's structured correctly.</span></span> <span data-ttu-id="dd552-112">La meilleure façon de valider un e-mail consiste à envoyer un e-mail de test à l’adresse.</span><span class="sxs-lookup"><span data-stu-id="dd552-112">The best way to validate an email is to send a test email to the address.</span></span>

[!INCLUDE [regex](../../../includes/regex.md)]

## <a name="example"></a><span data-ttu-id="dd552-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="dd552-113">Example</span></span>

<span data-ttu-id="dd552-114">L’exemple définit une `IsValidEmail` méthode qui retourne `true` si la chaîne contient une adresse de messagerie valide et, `false` si elle ne l’est pas, n’effectue aucune autre action.</span><span class="sxs-lookup"><span data-stu-id="dd552-114">The example defines an `IsValidEmail` method, which returns `true` if the string contains a valid email address and `false` if it doesn't, but takes no other action.</span></span>

<span data-ttu-id="dd552-115">Pour vérifier que l'adresse de messagerie est valide, la méthode `IsValidEmail` appelle la méthode <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> avec le modèle d'expression régulière `(@)(.+)$` pour séparer le nom de domaine de l'adresse de messagerie.</span><span class="sxs-lookup"><span data-stu-id="dd552-115">To verify that the email address is valid, the `IsValidEmail` method calls the <xref:System.Text.RegularExpressions.Regex.Replace%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.MatchEvaluator%29?displayProperty=nameWithType> method with the `(@)(.+)$` regular expression pattern to separate the domain name from the email address.</span></span> <span data-ttu-id="dd552-116">Le troisième paramètre est un délégué <xref:System.Text.RegularExpressions.MatchEvaluator> qui représente la méthode qui traite et remplace le texte correspondant.</span><span class="sxs-lookup"><span data-stu-id="dd552-116">The third parameter is a <xref:System.Text.RegularExpressions.MatchEvaluator> delegate that represents the method that processes and replaces the matched text.</span></span> <span data-ttu-id="dd552-117">Le modèle d'expression régulière est interprété comme suit.</span><span class="sxs-lookup"><span data-stu-id="dd552-117">The regular expression pattern is interpreted as follows.</span></span>

| <span data-ttu-id="dd552-118">Modèle</span><span class="sxs-lookup"><span data-stu-id="dd552-118">Pattern</span></span> | <span data-ttu-id="dd552-119">Description</span><span class="sxs-lookup"><span data-stu-id="dd552-119">Description</span></span>                                                                         |
|---------|-------------------------------------------------------------------------------------|
| `(@)`   | <span data-ttu-id="dd552-120">Correspond à l'arobase (@).</span><span class="sxs-lookup"><span data-stu-id="dd552-120">Match the @ character.</span></span> <span data-ttu-id="dd552-121">Cette partie est le premier groupe de capture.</span><span class="sxs-lookup"><span data-stu-id="dd552-121">This part is the first capturing group.</span></span>                           |
| `(.+)`  | <span data-ttu-id="dd552-122">Correspond à une ou plusieurs occurrences d'un caractère quelconque.</span><span class="sxs-lookup"><span data-stu-id="dd552-122">Match one or more occurrences of any character.</span></span> <span data-ttu-id="dd552-123">Cette partie est le deuxième groupe de capture.</span><span class="sxs-lookup"><span data-stu-id="dd552-123">This part is the second capturing group.</span></span> |
| `$`     | <span data-ttu-id="dd552-124">Termine la correspondance à la fin de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="dd552-124">End the match at the end of the string.</span></span>                                             |

<span data-ttu-id="dd552-125">Le nom de domaine avec le caractère @ est passé à la méthode `DomainMapper` , qui utilise la classe <xref:System.Globalization.IdnMapping> pour convertir les caractères Unicode situés en dehors de la plage de caractères US-ASCII au format Punycode.</span><span class="sxs-lookup"><span data-stu-id="dd552-125">The domain name along with the @ character is passed to the `DomainMapper` method, which uses the <xref:System.Globalization.IdnMapping> class to translate Unicode characters that are outside the US-ASCII character range to Punycode.</span></span> <span data-ttu-id="dd552-126">La méthode affecte également à l'indicateur `invalid` la valeur `True` si la méthode <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> détecte des caractères non valides dans le nom de domaine.</span><span class="sxs-lookup"><span data-stu-id="dd552-126">The method also sets the `invalid` flag to `True` if the <xref:System.Globalization.IdnMapping.GetAscii%2A?displayProperty=nameWithType> method detects any invalid characters in the domain name.</span></span> <span data-ttu-id="dd552-127">La méthode retourne le nom de domaine Punycode précédé du symbole @ à la méthode `IsValidEmail` .</span><span class="sxs-lookup"><span data-stu-id="dd552-127">The method returns the Punycode domain name preceded by the @ symbol to the `IsValidEmail` method.</span></span>

> [!TIP]
> <span data-ttu-id="dd552-128">Il est recommandé d’utiliser le `(@)(.+)$` modèle d’expression régulière simple pour normaliser le domaine, puis retourner une valeur indiquant qu’il a réussi ou échoué.</span><span class="sxs-lookup"><span data-stu-id="dd552-128">It's recommended that you use the simple `(@)(.+)$` regular expression pattern to normalize the domain and then return a value indicating that it passed or failed.</span></span> <span data-ttu-id="dd552-129">Toutefois, l’exemple de cet article explique comment utiliser une expression régulière pour valider l’e-mail.</span><span class="sxs-lookup"><span data-stu-id="dd552-129">However, the example in this article describes how to further use a regular expression to validate the email.</span></span> <span data-ttu-id="dd552-130">Quelle que soit la façon dont vous validez un e-mail, vous devez toujours envoyer un e-mail de test à l’adresse pour vous assurer qu’il existe.</span><span class="sxs-lookup"><span data-stu-id="dd552-130">Regardless of how you validate an email, you should always send a test email to the address to make sure it exists.</span></span>

<span data-ttu-id="dd552-131">La méthode `IsValidEmail` appelle alors la méthode <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> pour vérifier que l'adresse est conforme à un modèle d'expression régulière.</span><span class="sxs-lookup"><span data-stu-id="dd552-131">The `IsValidEmail` method then calls the <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%29?displayProperty=nameWithType> method to verify that the address conforms to a regular expression pattern.</span></span>

<span data-ttu-id="dd552-132">La `IsValidEmail` méthode détermine simplement si le format d’e-mail est valide pour une adresse de messagerie, mais ne valide pas l’existence de l’e-mail.</span><span class="sxs-lookup"><span data-stu-id="dd552-132">The `IsValidEmail` method merely determines whether the email format is valid for an email address, it doesn't validate that the email exists.</span></span> <span data-ttu-id="dd552-133">En outre, la `IsValidEmail` méthode ne vérifie pas si le nom de domaine de niveau supérieur est un nom de domaine valide figurant dans la [base de données de zone racine IANA](https://www.iana.org/domains/root/db), ce qui nécessite une opération de recherche.</span><span class="sxs-lookup"><span data-stu-id="dd552-133">Also, the `IsValidEmail` method doesn't verify that the top-level domain name is a valid domain name listed at the [IANA Root Zone Database](https://www.iana.org/domains/root/db), which would require a look-up operation.</span></span>

:::code language="csharp" source="snippets/how-to-verify-that-strings-are-in-valid-email-format/csharp/RegexUtilities.cs":::

:::code language="vb" source="snippets/how-to-verify-that-strings-are-in-valid-email-format/vb/RegexUtilities.vb":::

<span data-ttu-id="dd552-134">Dans cet exemple, le modèle d’expression régulière `^[^@\s]+@[^@\s]+\.[^@\s]+$` est interprété de la manière indiquée dans le tableau ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="dd552-134">In this example, the regular expression pattern `^[^@\s]+@[^@\s]+\.[^@\s]+$` is interpreted as shown in the following table.</span></span> <span data-ttu-id="dd552-135">L’expression régulière est compilée à l’aide de l' <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> indicateur.</span><span class="sxs-lookup"><span data-stu-id="dd552-135">The regular expression is compiled using the <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> flag.</span></span>

| <span data-ttu-id="dd552-136">Modèle</span><span class="sxs-lookup"><span data-stu-id="dd552-136">Pattern</span></span>   | <span data-ttu-id="dd552-137">Description</span><span class="sxs-lookup"><span data-stu-id="dd552-137">Description</span></span>                                                                              |
|-----------|------------------------------------------------------------------------------------------|
| `^`       | <span data-ttu-id="dd552-138">Commence la recherche de correspondance au début de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="dd552-138">Begin the match at the start of the string.</span></span>                                              |
| `[^@\s]+` | <span data-ttu-id="dd552-139">Correspond à une ou plusieurs occurrences d’un caractère autre que le caractère @ ou l’espace blanc.</span><span class="sxs-lookup"><span data-stu-id="dd552-139">Match one or more occurrences of any character other than the @ character or whitespace.</span></span> |
| `@`       | <span data-ttu-id="dd552-140">Correspond à l'arobase (@).</span><span class="sxs-lookup"><span data-stu-id="dd552-140">Match the @ character.</span></span>                                                                   |
| `[^@\s]+` | <span data-ttu-id="dd552-141">Correspond à une ou plusieurs occurrences d’un caractère autre que le caractère @ ou l’espace blanc.</span><span class="sxs-lookup"><span data-stu-id="dd552-141">Match one or more occurrences of any character other than the @ character or whitespace.</span></span> |
| `\.`      | <span data-ttu-id="dd552-142">Correspond à un caractère à point unique.</span><span class="sxs-lookup"><span data-stu-id="dd552-142">Match a single period character.</span></span>                                                         |
| `[^@\s]+` | <span data-ttu-id="dd552-143">Correspond à une ou plusieurs occurrences d’un caractère autre que le caractère @ ou l’espace blanc.</span><span class="sxs-lookup"><span data-stu-id="dd552-143">Match one or more occurrences of any character other than the @ character or whitespace.</span></span> |
| `$`       | <span data-ttu-id="dd552-144">Termine la correspondance à la fin de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="dd552-144">End the match at the end of the string.</span></span>                                                  |

> [!IMPORTANT]
> <span data-ttu-id="dd552-145">Cette expression régulière n’est pas destinée à couvrir tous les aspects d’une adresse de messagerie valide.</span><span class="sxs-lookup"><span data-stu-id="dd552-145">This regular expression is not intended to cover every aspect of a valid email address.</span></span> <span data-ttu-id="dd552-146">Il est fourni comme exemple pour que vous l’étendiez si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="dd552-146">It's provided as an example for you to extend as needed.</span></span>

## <a name="see-also"></a><span data-ttu-id="dd552-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd552-147">See also</span></span>

- [<span data-ttu-id="dd552-148">Expressions régulières .NET</span><span class="sxs-lookup"><span data-stu-id="dd552-148">.NET Regular Expressions</span></span>](regular-expressions.md)
- [<span data-ttu-id="dd552-149">Quelle est la durée d’une validation d’adresse de messagerie ?</span><span class="sxs-lookup"><span data-stu-id="dd552-149">How far should one take e-mail address validation?</span></span>](https://softwareengineering.stackexchange.com/questions/78353/how-far-should-one-take-e-mail-address-validation#78363)
