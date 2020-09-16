---
title: Validation de la complexité des mots de passe
ms.date: 07/20/2015
helpviewer_keywords:
- String data type [Visual Basic], validation
ms.assetid: 5d9a918f-6c1f-41a3-a019-b5c2b8ce0381
ms.openlocfilehash: 8cb04286e98cf78f0fb66dde92002ee09e2ea0f5
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556243"
---
# <a name="walkthrough-validating-that-passwords-are-complex-visual-basic"></a><span data-ttu-id="c531d-102">Procédure pas à pas : validation de la complexité des mots de passe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c531d-102">Walkthrough: Validating That Passwords Are Complex (Visual Basic)</span></span>
<span data-ttu-id="c531d-103">Cette méthode vérifie certaines caractéristiques de mot de passe fort et met à jour un paramètre de chaîne avec des informations sur la vérification de l’échec du mot de passe.</span><span class="sxs-lookup"><span data-stu-id="c531d-103">This method checks for some strong-password characteristics and updates a string parameter with information about which checks the password fails.</span></span>  
  
 <span data-ttu-id="c531d-104">Les mots de passe peuvent être utilisés dans un système sécurisé pour autoriser un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c531d-104">Passwords can be used in a secure system to authorize a user.</span></span> <span data-ttu-id="c531d-105">Toutefois, les mots de passe doivent être difficiles à deviner pour les utilisateurs non autorisés.</span><span class="sxs-lookup"><span data-stu-id="c531d-105">However, the passwords must be difficult for unauthorized users to guess.</span></span> <span data-ttu-id="c531d-106">Les attaquants peuvent utiliser un programme d' *attaque par dictionnaire* , qui itère au sein de tous les mots d’un dictionnaire (ou de plusieurs dictionnaires dans différentes langues) et teste si l’un des mots fonctionne en tant que mot de passe d’un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c531d-106">Attackers can use a *dictionary attack* program, which iterates through all of the words in a dictionary (or multiple dictionaries in different languages) and tests whether any of the words work as a user's password.</span></span> <span data-ttu-id="c531d-107">Des mots de passe faibles, tels que « Yankees » ou « Mustang », peuvent être devinés rapidement.</span><span class="sxs-lookup"><span data-stu-id="c531d-107">Weak passwords such as "Yankees" or "Mustang" can be guessed quickly.</span></span> <span data-ttu-id="c531d-108">Des mots de passe plus forts, tels que « ? « L1N3vaFiNdMeyeP@sSWerd ! » Sont très moins susceptibles d’être devinés.</span><span class="sxs-lookup"><span data-stu-id="c531d-108">Stronger passwords, such as "?You'L1N3vaFiNdMeyeP@sSWerd!", are much less likely to be guessed.</span></span> <span data-ttu-id="c531d-109">Un système protégé par mot de passe doit s’assurer que les utilisateurs choisissent des mots de passe forts.</span><span class="sxs-lookup"><span data-stu-id="c531d-109">A password-protected system should ensure that users choose strong passwords.</span></span>  
  
 <span data-ttu-id="c531d-110">Un mot de passe fort est complexe (contenant un mélange de majuscules, de minuscules, de chiffres et de caractères spéciaux) et n’est pas un mot.</span><span class="sxs-lookup"><span data-stu-id="c531d-110">A strong password is complex (containing a mixture of uppercase, lowercase, numeric, and special characters) and is not a word.</span></span> <span data-ttu-id="c531d-111">Cet exemple montre comment vérifier la complexité.</span><span class="sxs-lookup"><span data-stu-id="c531d-111">This example demonstrates how to verify complexity.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c531d-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="c531d-112">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="c531d-113">Code</span><span class="sxs-lookup"><span data-stu-id="c531d-113">Code</span></span>  
 [!code-vb[VbVbcnRegEx#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnRegEx/VB/Class1.vb#1)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="c531d-114">Compiler le code</span><span class="sxs-lookup"><span data-stu-id="c531d-114">Compile the code</span></span>  
 <span data-ttu-id="c531d-115">Appelez cette méthode en passant la chaîne qui contient ce mot de passe.</span><span class="sxs-lookup"><span data-stu-id="c531d-115">Call this method by passing the string that contains that password.</span></span>  
  
 <span data-ttu-id="c531d-116">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="c531d-116">This example requires:</span></span>  
  
- <span data-ttu-id="c531d-117">Un accès aux membres de l’espace de noms <xref:System.Text.RegularExpressions>.</span><span class="sxs-lookup"><span data-stu-id="c531d-117">Access to the members of the <xref:System.Text.RegularExpressions> namespace.</span></span> <span data-ttu-id="c531d-118">Ajoutez une instruction `Imports` si vous n’utilisez pas de noms de membres qualifiés complets dans votre code.</span><span class="sxs-lookup"><span data-stu-id="c531d-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="c531d-119">Pour plus d’informations, consultez [Instruction Imports (espace de noms et type .NET)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="c531d-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="security"></a><span data-ttu-id="c531d-120">Sécurité</span><span class="sxs-lookup"><span data-stu-id="c531d-120">Security</span></span>  
 <span data-ttu-id="c531d-121">Si vous déplacez le mot de passe sur un réseau, vous devez utiliser une méthode sécurisée pour le transfert des données.</span><span class="sxs-lookup"><span data-stu-id="c531d-121">If you're moving the password across a network, you need to use a secure method for transferring data.</span></span> <span data-ttu-id="c531d-122">Pour plus d’informations, consultez [sécurité des applications Web ASP.net](/previous-versions/aspnet/330a99hc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c531d-122">For more information, see [ASP.NET Web Application Security](/previous-versions/aspnet/330a99hc(v=vs.100)).</span></span>
  
 <span data-ttu-id="c531d-123">Vous pouvez améliorer la précision de la `ValidatePassword` fonction en ajoutant des vérifications de complexité supplémentaires :</span><span class="sxs-lookup"><span data-stu-id="c531d-123">You can improve the accuracy of the `ValidatePassword` function by adding additional complexity checks:</span></span>  
  
- <span data-ttu-id="c531d-124">Comparez le mot de passe et ses sous-chaînes avec le nom de l’utilisateur, l’identificateur de l’utilisateur et un dictionnaire défini par l’application.</span><span class="sxs-lookup"><span data-stu-id="c531d-124">Compare the password and its substrings against the user's name, user identifier, and an application-defined dictionary.</span></span> <span data-ttu-id="c531d-125">En outre, traitez les caractères similaires visuellement comme équivalents lors de l’exécution des comparaisons.</span><span class="sxs-lookup"><span data-stu-id="c531d-125">In addition, treat visually similar characters as equivalent when performing the comparisons.</span></span> <span data-ttu-id="c531d-126">Par exemple, considérez les lettres « l » et « e » comme équivalentes aux chiffres « 1 » et « 3 ».</span><span class="sxs-lookup"><span data-stu-id="c531d-126">For example, treat the letters "l" and "e" as equivalent to the numerals "1" and "3".</span></span>  
  
- <span data-ttu-id="c531d-127">S’il n’y a qu’un seul caractère majuscule, assurez-vous qu’il ne s’agit pas du premier caractère du mot de passe.</span><span class="sxs-lookup"><span data-stu-id="c531d-127">If there is only one uppercase character, make sure it is not the password's first character.</span></span>  
  
- <span data-ttu-id="c531d-128">Assurez-vous que les deux derniers caractères du mot de passe sont des caractères alphabétiques.</span><span class="sxs-lookup"><span data-stu-id="c531d-128">Make sure that the last two characters of the password are letter characters.</span></span>  
  
- <span data-ttu-id="c531d-129">N’autorisez pas les mots de passe dans lesquels tous les symboles sont entrés à partir de la ligne supérieure du clavier.</span><span class="sxs-lookup"><span data-stu-id="c531d-129">Do not allow passwords in which all the symbols are entered from the keyboard's top row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c531d-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c531d-130">See also</span></span>

- <xref:System.Text.RegularExpressions.Regex>
- <span data-ttu-id="c531d-131">[Sécurité des applications web ASP.NET](/previous-versions/aspnet/330a99hc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c531d-131">[ASP.NET Web Application Security](/previous-versions/aspnet/330a99hc(v=vs.100))</span></span>
