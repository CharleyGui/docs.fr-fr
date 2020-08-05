---
title: Sécurité et entrées d'utilisateur
description: Votre code peut passer des données entrées par l’utilisateur en tant que paramètres à un autre code, ce qui peut affecter la sécurité. Vous pouvez effectuer une vérification de plage pour rejeter les entrées problématiques.
ms.date: 07/15/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
ms.openlocfilehash: e46bf8e653567637b4e6236849981fdb32df447c
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555940"
---
# <a name="security-and-user-input"></a><span data-ttu-id="87d0b-104">Sécurité et entrées d'utilisateur</span><span class="sxs-lookup"><span data-stu-id="87d0b-104">Security and User Input</span></span>

<span data-ttu-id="87d0b-105">Les données utilisateurs, quel que soit le type d’entrée (données d’une demande web ou URL, entrée de commandes d’une application Windows Forms, etc.), peuvent affecter négativement le code, dans la mesure où ces données sont souvent utilisées directement en tant que paramètres pour appeler un autre code.</span><span class="sxs-lookup"><span data-stu-id="87d0b-105">User data, which is any kind of input (data from a Web request or URL, input to controls of a Microsoft Windows Forms application, and so on), can adversely influence code because often that data is used directly as parameters to call other code.</span></span> <span data-ttu-id="87d0b-106">Cette situation, similaire à l’appel de votre code par du code malveillant à l’aide de paramètres étranges, nécessite les mêmes précautions.</span><span class="sxs-lookup"><span data-stu-id="87d0b-106">This situation is analogous to malicious code calling your code with strange parameters, and the same precautions should be taken.</span></span> <span data-ttu-id="87d0b-107">En réalité, une entrée utilisateur est plus difficile à sécuriser, car il n’existe aucune frame de pile permettant de détecter la présence de données potentiellement non fiables.</span><span class="sxs-lookup"><span data-stu-id="87d0b-107">User input is actually harder to make safe because there is no stack frame to trace the presence of the potentially untrusted data.</span></span>

<span data-ttu-id="87d0b-108">Il s’agit des bogues de sécurité les plus subtils et les plus difficiles à identifier car, bien qu’ils peuvent apparaître dans du code en apparence non lié à la sécurité, ils constituent une passerelle permettant de transférer des données incorrectes vers d’autres codes.</span><span class="sxs-lookup"><span data-stu-id="87d0b-108">These are among the subtlest and hardest security bugs to find because, although they can exist in code that is seemingly unrelated to security, they are a gateway to pass bad data through to other code.</span></span> <span data-ttu-id="87d0b-109">Pour rechercher ces bogues, suivez tout type de données d’entrée, imaginez la fourchette de valeurs possibles, et déterminez si le code traitant ces données peut traiter l’ensemble des cas.</span><span class="sxs-lookup"><span data-stu-id="87d0b-109">To look for these bugs, follow any kind of input data, imagine what the range of possible values might be, and consider whether the code seeing this data can handle all those cases.</span></span> <span data-ttu-id="87d0b-110">Pour corriger ces bogues, procédez à une vérification de plage, puis rejetez toute entrée ne pouvant pas être traitée par le code.</span><span class="sxs-lookup"><span data-stu-id="87d0b-110">You can fix these bugs through range checking and rejecting any input the code cannot handle.</span></span>

<span data-ttu-id="87d0b-111">Voici quelques considérations importantes associées aux données utilisateurs :</span><span class="sxs-lookup"><span data-stu-id="87d0b-111">Some important considerations involving user data include the following:</span></span>

- <span data-ttu-id="87d0b-112">Toutes les données utilisateur d’une réponse de serveur s’exécutent dans le contexte du site du serveur sur le client.</span><span class="sxs-lookup"><span data-stu-id="87d0b-112">Any user data in a server response runs in the context of the server's site on the client.</span></span> <span data-ttu-id="87d0b-113">Si votre serveur Web utilise des données utilisateur et les insère dans la page Web renvoyée, il peut, par exemple, inclure une **\<script>** balise et l’exécuter comme si elle était à partir du serveur.</span><span class="sxs-lookup"><span data-stu-id="87d0b-113">If your Web server takes user data and inserts it into the returned Web page, it might, for example, include a **\<script>** tag and run as if from the server.</span></span>

- <span data-ttu-id="87d0b-114">N’oubliez pas que le client peut demander toute URL.</span><span class="sxs-lookup"><span data-stu-id="87d0b-114">Remember that the client can request any URL.</span></span>

- <span data-ttu-id="87d0b-115">Tenez compte des chemins d’accès délicats ou non valides :</span><span class="sxs-lookup"><span data-stu-id="87d0b-115">Consider tricky or invalid paths:</span></span>

  - <span data-ttu-id="87d0b-116">..\ , des chemins d’accès extrêmement longs.</span><span class="sxs-lookup"><span data-stu-id="87d0b-116">..\ , extremely long paths.</span></span>

  - <span data-ttu-id="87d0b-117">Utilisation de caractères génériques (\*).</span><span class="sxs-lookup"><span data-stu-id="87d0b-117">Use of wild card characters (\*).</span></span>

  - <span data-ttu-id="87d0b-118">Expansion de jeton (%token%).</span><span class="sxs-lookup"><span data-stu-id="87d0b-118">Token expansion (%token%).</span></span>

  - <span data-ttu-id="87d0b-119">Formes étranges de chemins d’accès présentant une signification spécifique.</span><span class="sxs-lookup"><span data-stu-id="87d0b-119">Strange forms of paths with special meaning.</span></span>

  - <span data-ttu-id="87d0b-120">Autres noms de flux de système de fichiers, comme `filename::$DATA`.</span><span class="sxs-lookup"><span data-stu-id="87d0b-120">Alternate file system stream names such as `filename::$DATA`.</span></span>

  - <span data-ttu-id="87d0b-121">Versions courtes de noms de fichiers, comme `longfi~1` pour `longfilename`.</span><span class="sxs-lookup"><span data-stu-id="87d0b-121">Short versions of file names such as `longfi~1` for `longfilename`.</span></span>

- <span data-ttu-id="87d0b-122">N’oubliez pas que la commande Eval(userdata) peut effectuer tout type d’action.</span><span class="sxs-lookup"><span data-stu-id="87d0b-122">Remember that Eval(userdata) can do anything.</span></span>

- <span data-ttu-id="87d0b-123">Méfiez-vous de toute liaison tardive vers un nom comprenant des données utilisateur.</span><span class="sxs-lookup"><span data-stu-id="87d0b-123">Be wary of late binding to a name that includes some user data.</span></span>

- <span data-ttu-id="87d0b-124">Si vous traitez des données web, tenez compte des différents types d’échappements autorisés, notamment des suivants :</span><span class="sxs-lookup"><span data-stu-id="87d0b-124">If you are dealing with Web data, consider the various forms of escapes that are permissible, including:</span></span>

  - <span data-ttu-id="87d0b-125">Échappements haxadécimaux (%nn).</span><span class="sxs-lookup"><span data-stu-id="87d0b-125">Hexadecimal escapes (%nn).</span></span>

  - <span data-ttu-id="87d0b-126">Échappements Unicode (%nnn).</span><span class="sxs-lookup"><span data-stu-id="87d0b-126">Unicode escapes (%nnn).</span></span>

  - <span data-ttu-id="87d0b-127">Échappements UTF-8 longs (%nn%nn).</span><span class="sxs-lookup"><span data-stu-id="87d0b-127">Overlong UTF-8 escapes (%nn%nn).</span></span>

  - <span data-ttu-id="87d0b-128">Doubles échappements (%nn devient %mmnn, où %mm est l’échappement de %).</span><span class="sxs-lookup"><span data-stu-id="87d0b-128">Double escapes (%nn becomes %mmnn, where %mm is the escape for '%').</span></span>

- <span data-ttu-id="87d0b-129">Méfiez-vous des noms utilisateur pouvant présenter plusieurs formats canoniques.</span><span class="sxs-lookup"><span data-stu-id="87d0b-129">Be wary of user names that might have more than one canonical format.</span></span> <span data-ttu-id="87d0b-130">Par exemple, bien souvent, vous pouvez utiliser le format MONDOMAINE\\*nomutilisateur* ou le format *nomutilisateur*@mydomain.example.com.</span><span class="sxs-lookup"><span data-stu-id="87d0b-130">For example, you can often use either the MYDOMAIN\\*username* form or the *username*@mydomain.example.com form.</span></span>

## <a name="see-also"></a><span data-ttu-id="87d0b-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87d0b-131">See also</span></span>

- [<span data-ttu-id="87d0b-132">Instructions de codage sécurisé</span><span class="sxs-lookup"><span data-stu-id="87d0b-132">Secure Coding Guidelines</span></span>](secure-coding-guidelines.md)
- [<span data-ttu-id="87d0b-133">Sécurité ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="87d0b-133">ASP.NET Core Security</span></span>](/aspnet/core/security/)
