---
title: -errorreport
ms.date: 08/14/2018
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
ms.openlocfilehash: a9741f7a8283f8603e02dae5abea151c6ee5d75e
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775665"
---
# <a name="-errorreport"></a><span data-ttu-id="38e7a-102">-errorreport</span><span class="sxs-lookup"><span data-stu-id="38e7a-102">-errorreport</span></span>

<span data-ttu-id="38e7a-103">Spécifie comment le compilateur Visual Basic doit signaler les erreurs internes du compilateur.</span><span class="sxs-lookup"><span data-stu-id="38e7a-103">Specifies how the Visual Basic compiler should report internal compiler errors.</span></span>

## <a name="syntax"></a><span data-ttu-id="38e7a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38e7a-104">Syntax</span></span>

```console
-errorreport:{ prompt | queue | send | none }
```

## <a name="remarks"></a><span data-ttu-id="38e7a-105">Notes</span><span class="sxs-lookup"><span data-stu-id="38e7a-105">Remarks</span></span>

<span data-ttu-id="38e7a-106">Cette option offre un moyen pratique de signaler un Visual Basic erreur interne du compilateur (ICE) à l’équipe Visual Basic chez Microsoft.</span><span class="sxs-lookup"><span data-stu-id="38e7a-106">This option provides a convenient way to report a Visual Basic internal compiler error (ICE) to the Visual Basic team at Microsoft.</span></span> <span data-ttu-id="38e7a-107">Par défaut, le compilateur n’envoie aucune information à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="38e7a-107">By default, the compiler sends no information to Microsoft.</span></span> <span data-ttu-id="38e7a-108">Toutefois, si vous rencontrez une erreur interne du compilateur, cette option vous permet de signaler l’erreur à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="38e7a-108">However, if you do encounter an internal compiler error, this option allows you to report the error to Microsoft.</span></span> <span data-ttu-id="38e7a-109">Ces informations permettront aux ingénieurs Microsoft d’identifier la cause et peuvent contribuer à améliorer la prochaine version de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="38e7a-109">That information will help Microsoft engineers identify the cause and may help improve the next release of Visual Basic.</span></span>

<span data-ttu-id="38e7a-110">La capacité d’un utilisateur à envoyer des rapports dépend des autorisations de la stratégie de l’ordinateur et de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="38e7a-110">A user's ability to send reports depends on machine and user policy permissions.</span></span>

<span data-ttu-id="38e7a-111">Le tableau suivant résume l’effet de l’option `-errorreport`.</span><span class="sxs-lookup"><span data-stu-id="38e7a-111">The following table summarizes the effect of the `-errorreport` option.</span></span>

|<span data-ttu-id="38e7a-112">Option</span><span class="sxs-lookup"><span data-stu-id="38e7a-112">Option</span></span>|<span data-ttu-id="38e7a-113">Comportement</span><span class="sxs-lookup"><span data-stu-id="38e7a-113">Behavior</span></span>|
|---|---|
|`prompt`|<span data-ttu-id="38e7a-114">Si une erreur interne du compilateur se produit, une boîte de dialogue s’affiche pour vous permettre d’afficher les données exactes collectées par le compilateur.</span><span class="sxs-lookup"><span data-stu-id="38e7a-114">If an internal compiler error occurs, a dialog box comes up so that you can view the exact data that the compiler collected.</span></span> <span data-ttu-id="38e7a-115">Vous pouvez déterminer s’il existe des informations sensibles dans le rapport d’erreurs et si vous souhaitez les envoyer à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="38e7a-115">You can determine if there is any sensitive information in the error report and make a decision on whether to send it to Microsoft.</span></span> <span data-ttu-id="38e7a-116">Si vous décidez de l’envoyer et que les paramètres de stratégie de l’ordinateur et de l’utilisateur l’autorisent, le compilateur envoie les données à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="38e7a-116">If you decide to send it, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span>|
|`queue`|<span data-ttu-id="38e7a-117">Met le rapport d’erreurs en file d’attente.</span><span class="sxs-lookup"><span data-stu-id="38e7a-117">Queues the error report.</span></span> <span data-ttu-id="38e7a-118">Lorsque vous vous connectez avec des privilèges d’administrateur, vous pouvez signaler les échecs depuis la dernière connexion (vous n’êtes pas invité à envoyer des rapports pour les défaillances plus d’une fois tous les trois jours).</span><span class="sxs-lookup"><span data-stu-id="38e7a-118">When you log in with administrator privileges, you can report any failures since the last time you were logged in (you will not be prompted to send reports for failures more than once every three days).</span></span> <span data-ttu-id="38e7a-119">Il s’agit du comportement par défaut lorsque l’option `-errorreport` n’est pas spécifiée.</span><span class="sxs-lookup"><span data-stu-id="38e7a-119">This is the default behavior when the `-errorreport` option is not specified.</span></span>|
|`send`|<span data-ttu-id="38e7a-120">Si une erreur interne du compilateur se produit et que les paramètres de stratégie de l’ordinateur et de l’utilisateur l’autorisent, le compilateur envoie les données à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="38e7a-120">If an internal compiler error occurs, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span><br /><br /> <span data-ttu-id="38e7a-121">L’option `-errorreport:send` tente d’envoyer automatiquement des informations sur les erreurs à Microsoft si la création de rapports est activée par les paramètres du système [rapport d’erreurs Windows](/windows/desktop/wer/windows-error-reporting) .</span><span class="sxs-lookup"><span data-stu-id="38e7a-121">The option `-errorreport:send` attempts to automatically send error information to Microsoft if reporting is enabled by the [Windows Error Reporting](/windows/desktop/wer/windows-error-reporting) system settings.</span></span> |
|`none`|<span data-ttu-id="38e7a-122">Si une erreur interne du compilateur se produit, elle n’est pas collectée ou envoyée à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="38e7a-122">If an internal compiler error occurs, it will not be collected or sent to Microsoft.</span></span>|

<span data-ttu-id="38e7a-123">Le compilateur envoie des données qui incluent la pile au moment de l’erreur, qui comprend généralement du code source.</span><span class="sxs-lookup"><span data-stu-id="38e7a-123">The compiler sends data that includes the stack at the time of the error, which usually includes some source code.</span></span> <span data-ttu-id="38e7a-124">Si `-errorreport` est utilisé avec l’option [-bugreport (](../../../visual-basic/reference/command-line-compiler/bugreport.md) , alors l’intégralité du fichier source est envoyée.</span><span class="sxs-lookup"><span data-stu-id="38e7a-124">If `-errorreport` is used with the [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, then the entire source file is sent.</span></span>

<span data-ttu-id="38e7a-125">Cette option est utilisée de manière optimale avec l’option [-bugreport (](../../../visual-basic/reference/command-line-compiler/bugreport.md) , car elle permet aux ingénieurs Microsoft de reproduire plus facilement l’erreur.</span><span class="sxs-lookup"><span data-stu-id="38e7a-125">This option is best used with the [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, because it allows Microsoft engineers to more easily reproduce the error.</span></span>

> [!NOTE]
> <span data-ttu-id="38e7a-126">L’option `-errorreport` n’est pas disponible dans l’environnement de développement Visual Studio. elle est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="38e7a-126">The `-errorreport` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="38e7a-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="38e7a-127">Example</span></span>

<span data-ttu-id="38e7a-128">Le code suivant tente de compiler `T2.vb`, et si le compilateur rencontre une erreur interne du compilateur, il vous invite à envoyer le rapport d’erreurs à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="38e7a-128">The following code attempts to compile `T2.vb`, and if the compiler encounters an internal compiler error, it prompts you to send the error report to Microsoft.</span></span>

```console
vbc -errorreport:prompt t2.vb
```

## <a name="see-also"></a><span data-ttu-id="38e7a-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38e7a-129">See also</span></span>

- [<span data-ttu-id="38e7a-130">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="38e7a-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="38e7a-131">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="38e7a-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="38e7a-132">-bugreport</span><span class="sxs-lookup"><span data-stu-id="38e7a-132">-bugreport</span></span>](../../../visual-basic/reference/command-line-compiler/bugreport.md)
