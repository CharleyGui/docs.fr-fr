---
description: -errorreport (Options du compilateur C#)
title: -errorreport (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
ms.openlocfilehash: 6238ac392ff99d18d9cc7ea07e23b08ff235c14f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173228"
---
# <a name="-errorreport-c-compiler-options"></a><span data-ttu-id="ba7c0-103">-errorreport (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="ba7c0-103">-errorreport (C# Compiler Options)</span></span>

<span data-ttu-id="ba7c0-104">Cette option fournit un moyen pratique de signaler une erreur interne du compilateur C# à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ba7c0-104">This option provides a convenient way to report a C# internal compiler error to Microsoft.</span></span>

> [!NOTE]
> <span data-ttu-id="ba7c0-105">Sur Windows Vista et Windows Server 2008, les paramètres de rapport d’erreurs que vous spécifiez pour Visual Studio ne remplacent pas les paramètres définis par l’intermédiaire de Rapport d’erreurs Windows.</span><span class="sxs-lookup"><span data-stu-id="ba7c0-105">On Windows Vista and Windows Server 2008, the error reporting settings that you make for Visual Studio do not override the settings made through Windows Error Reporting (WER).</span></span> <span data-ttu-id="ba7c0-106">Les paramètres de Rapport d’erreurs Windows ont toujours priorité sur les paramètres de signalement d’erreurs de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ba7c0-106">WER settings always take precedence over Visual Studio error reporting settings.</span></span>

## <a name="syntax"></a><span data-ttu-id="ba7c0-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba7c0-107">Syntax</span></span>

```console
-errorreport:{ none | prompt | queue | send }
```

## <a name="arguments"></a><span data-ttu-id="ba7c0-108">Arguments</span><span class="sxs-lookup"><span data-stu-id="ba7c0-108">Arguments</span></span>

 <span data-ttu-id="ba7c0-109">**Aucune**</span><span class="sxs-lookup"><span data-stu-id="ba7c0-109">**none**</span></span>  
 <span data-ttu-id="ba7c0-110">Les rapports sur les erreurs internes du compilateur ne seront pas collectés ni envoyés à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ba7c0-110">Reports about internal compiler errors will not be collected or sent to Microsoft.</span></span>

 <span data-ttu-id="ba7c0-111">**invite** Vous invite à envoyer un rapport lorsque vous recevez une erreur interne du compilateur.</span><span class="sxs-lookup"><span data-stu-id="ba7c0-111">**prompt** Prompts you to send a report when you receive an internal compiler error.</span></span> <span data-ttu-id="ba7c0-112">**prompt** est la valeur par défaut quand vous compilez une application dans l’environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="ba7c0-112">**prompt** is the default when you compile an application in the development environment.</span></span>

 <span data-ttu-id="ba7c0-113">**file d’attente** Met en file d’attente le rapport d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="ba7c0-113">**queue** Queues the error report.</span></span> <span data-ttu-id="ba7c0-114">Quand vous ouvrez une session avec des informations d’identification administratives, vous pouvez signaler toute défaillance qui s’est produite depuis votre dernière connexion.</span><span class="sxs-lookup"><span data-stu-id="ba7c0-114">When you log on with administrative credentials, you can report any failures since the last time that you were logged on.</span></span> <span data-ttu-id="ba7c0-115">Vous ne serez pas invité à envoyer des rapports d’échecs plus d’une fois tous les trois jours.</span><span class="sxs-lookup"><span data-stu-id="ba7c0-115">You will not be prompted to send reports for failures more than once every three days.</span></span> <span data-ttu-id="ba7c0-116">**queue** est la valeur par défaut quand vous compilez une application à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="ba7c0-116">**queue** is the default when you compile an application at the command line.</span></span>

 <span data-ttu-id="ba7c0-117">**Envoyer** Envoie automatiquement des rapports d’erreurs internes du compilateur à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ba7c0-117">**send** Automatically sends reports of internal compiler errors to Microsoft.</span></span> <span data-ttu-id="ba7c0-118">Pour activer cette option, vous devez tout d’abord accepter la politique de collecte de données de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ba7c0-118">To enable this option, you must first agree to the Microsoft data collection policy.</span></span> <span data-ttu-id="ba7c0-119">La première fois que vous spécifiez **-errorreport:send** sur un ordinateur, un message du compilateur vous dirige vers un site web qui affiche la politique de collecte de données de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ba7c0-119">The first time that you specify **-errorreport:send** on a computer, a compiler message will refer you to a Web site that contains the Microsoft data collection policy.</span></span>

## <a name="remarks"></a><span data-ttu-id="ba7c0-120">Notes</span><span class="sxs-lookup"><span data-stu-id="ba7c0-120">Remarks</span></span>

 <span data-ttu-id="ba7c0-121">Une erreur interne du compilateur se produit quand le compilateur ne peut pas traiter un fichier de code source.</span><span class="sxs-lookup"><span data-stu-id="ba7c0-121">An internal compiler error (ICE) results when the compiler cannot process a source code file.</span></span> <span data-ttu-id="ba7c0-122">Quand une telle erreur se produit, le compilateur ne génère pas de fichier de sortie ni de diagnostic utile que vous pouvez utiliser pour corriger votre code.</span><span class="sxs-lookup"><span data-stu-id="ba7c0-122">When an ICE occurs, the compiler does not produce an output file or any useful diagnostic that you can use to fix your code.</span></span>

 <span data-ttu-id="ba7c0-123">Dans les versions précédentes, quand vous receviez une erreur interne du compilateur, vous étiez invité à contacter le Support technique Microsoft pour signaler le problème.</span><span class="sxs-lookup"><span data-stu-id="ba7c0-123">In previous releases, when you received an ICE, you were encouraged to contact Microsoft Product Support Services to report the problem.</span></span> <span data-ttu-id="ba7c0-124">En utilisant **-errorreport**, vous pouvez fournir des informations sur l’erreur interne du compilateur à l’équipe Visual C#.</span><span class="sxs-lookup"><span data-stu-id="ba7c0-124">By using **-errorreport**, you can provide ICE information to the Visual C# team.</span></span> <span data-ttu-id="ba7c0-125">Vos rapports d’erreurs peuvent aider à améliorer les versions ultérieures du compilateur.</span><span class="sxs-lookup"><span data-stu-id="ba7c0-125">Your error reports can help improve future compiler releases.</span></span>

 <span data-ttu-id="ba7c0-126">La capacité d’un utilisateur à envoyer des rapports dépend des autorisations de stratégie ordinateur et utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ba7c0-126">A user's ability to send reports depends on computer and user policy permissions.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="ba7c0-127">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ba7c0-127">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="ba7c0-128">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="ba7c0-128">Open the project's **Properties** page.</span></span> <span data-ttu-id="ba7c0-129">Pour plus d’informations, consultez [Générer, page du Concepteur de projets (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="ba7c0-129">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>

2. <span data-ttu-id="ba7c0-130">Cliquez sur la page de propriétés **Générer**.</span><span class="sxs-lookup"><span data-stu-id="ba7c0-130">Click the **Build** property page.</span></span>

3. <span data-ttu-id="ba7c0-131">Cliquez sur le bouton **Avancé** .</span><span class="sxs-lookup"><span data-stu-id="ba7c0-131">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="ba7c0-132">Modifiez la propriété **Rapport d’erreurs du compilateur interne**.</span><span class="sxs-lookup"><span data-stu-id="ba7c0-132">Modify the **Internal Compiler Error Reporting** property.</span></span>

 <span data-ttu-id="ba7c0-133">Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span><span class="sxs-lookup"><span data-stu-id="ba7c0-133">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="ba7c0-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba7c0-134">See also</span></span>

- [<span data-ttu-id="ba7c0-135">Options du compilateur C#</span><span class="sxs-lookup"><span data-stu-id="ba7c0-135">C# Compiler Options</span></span>](./index.md)
