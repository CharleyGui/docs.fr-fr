---
title: -errorreport (Options du compilateur C#)
ms.date: 07/20/2015
f1_keywords:
- /errorreport
helpviewer_keywords:
- -errorreport compiler option [C#]
- errorreport compiler option [C#]
- /errorreport compiler option [C#]
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
ms.openlocfilehash: 52b58aac5e82d4228dfda9c4d77c1d1c5de3e0cd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253890"
---
# <a name="-errorreport-c-compiler-options"></a><span data-ttu-id="442d9-102">-errorreport (Options du compilateur C#)</span><span class="sxs-lookup"><span data-stu-id="442d9-102">-errorreport (C# Compiler Options)</span></span>
<span data-ttu-id="442d9-103">Cette option fournit un moyen pratique de signaler une erreur interne du compilateur C# à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="442d9-103">This option provides a convenient way to report a C# internal compiler error to Microsoft.</span></span>

> [!NOTE]
> <span data-ttu-id="442d9-104">Sur Windows Vista et Windows Server 2008, les paramètres de rapport d’erreurs que vous spécifiez pour Visual Studio ne remplacent pas les paramètres définis par l’intermédiaire de Rapport d’erreurs Windows.</span><span class="sxs-lookup"><span data-stu-id="442d9-104">On Windows Vista and Windows Server 2008, the error reporting settings that you make for Visual Studio do not override the settings made through Windows Error Reporting (WER).</span></span> <span data-ttu-id="442d9-105">Les paramètres de Rapport d’erreurs Windows ont toujours priorité sur les paramètres de signalement d’erreurs de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="442d9-105">WER settings always take precedence over Visual Studio error reporting settings.</span></span>

## <a name="syntax"></a><span data-ttu-id="442d9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="442d9-106">Syntax</span></span>

```console
-errorreport:{ none | prompt | queue | send }
```

## <a name="arguments"></a><span data-ttu-id="442d9-107">Arguments</span><span class="sxs-lookup"><span data-stu-id="442d9-107">Arguments</span></span>
 <span data-ttu-id="442d9-108">**aucun**</span><span class="sxs-lookup"><span data-stu-id="442d9-108">**none**</span></span>  
 <span data-ttu-id="442d9-109">Les rapports sur les erreurs internes du compilateur ne seront pas collectés ni envoyés à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="442d9-109">Reports about internal compiler errors will not be collected or sent to Microsoft.</span></span>

 <span data-ttu-id="442d9-110">**invite** Vous invite à envoyer un rapport lorsque vous recevez une erreur interne de compilateur.</span><span class="sxs-lookup"><span data-stu-id="442d9-110">**prompt** Prompts you to send a report when you receive an internal compiler error.</span></span> <span data-ttu-id="442d9-111">**prompt** est la valeur par défaut quand vous compilez une application dans l’environnement de développement.</span><span class="sxs-lookup"><span data-stu-id="442d9-111">**prompt** is the default when you compile an application in the development environment.</span></span>

 <span data-ttu-id="442d9-112">**file d’attente** Files d’attente le rapport d’erreur.</span><span class="sxs-lookup"><span data-stu-id="442d9-112">**queue** Queues the error report.</span></span> <span data-ttu-id="442d9-113">Quand vous ouvrez une session avec des informations d’identification administratives, vous pouvez signaler toute défaillance qui s’est produite depuis votre dernière connexion.</span><span class="sxs-lookup"><span data-stu-id="442d9-113">When you log on with administrative credentials, you can report any failures since the last time that you were logged on.</span></span> <span data-ttu-id="442d9-114">Vous ne serez pas invité à envoyer des rapports d’échecs plus d’une fois tous les trois jours.</span><span class="sxs-lookup"><span data-stu-id="442d9-114">You will not be prompted to send reports for failures more than once every three days.</span></span> <span data-ttu-id="442d9-115">**queue** est la valeur par défaut quand vous compilez une application à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="442d9-115">**queue** is the default when you compile an application at the command line.</span></span>

 <span data-ttu-id="442d9-116">**envoyer** Envoie automatiquement des rapports d’erreurs de compilateur interne à Microsoft.</span><span class="sxs-lookup"><span data-stu-id="442d9-116">**send** Automatically sends reports of internal compiler errors to Microsoft.</span></span> <span data-ttu-id="442d9-117">Pour activer cette option, vous devez tout d’abord accepter la politique de collecte de données de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="442d9-117">To enable this option, you must first agree to the Microsoft data collection policy.</span></span> <span data-ttu-id="442d9-118">La première fois que vous spécifiez **-errorreport:send** sur un ordinateur, un message du compilateur vous dirige vers un site web qui affiche la politique de collecte de données de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="442d9-118">The first time that you specify **-errorreport:send** on a computer, a compiler message will refer you to a Web site that contains the Microsoft data collection policy.</span></span>

## <a name="remarks"></a><span data-ttu-id="442d9-119">Notes </span><span class="sxs-lookup"><span data-stu-id="442d9-119">Remarks</span></span>
 <span data-ttu-id="442d9-120">Une erreur interne du compilateur se produit quand le compilateur ne peut pas traiter un fichier de code source.</span><span class="sxs-lookup"><span data-stu-id="442d9-120">An internal compiler error (ICE) results when the compiler cannot process a source code file.</span></span> <span data-ttu-id="442d9-121">Quand une telle erreur se produit, le compilateur ne génère pas de fichier de sortie ni de diagnostic utile que vous pouvez utiliser pour corriger votre code.</span><span class="sxs-lookup"><span data-stu-id="442d9-121">When an ICE occurs, the compiler does not produce an output file or any useful diagnostic that you can use to fix your code.</span></span>

 <span data-ttu-id="442d9-122">Dans les versions précédentes, quand vous receviez une erreur interne du compilateur, vous étiez invité à contacter le Support technique Microsoft pour signaler le problème.</span><span class="sxs-lookup"><span data-stu-id="442d9-122">In previous releases, when you received an ICE, you were encouraged to contact Microsoft Product Support Services to report the problem.</span></span> <span data-ttu-id="442d9-123">En utilisant **-errorreport**, vous pouvez fournir des informations sur l’erreur interne du compilateur à l’équipe Visual C#.</span><span class="sxs-lookup"><span data-stu-id="442d9-123">By using **-errorreport**, you can provide ICE information to the Visual C# team.</span></span> <span data-ttu-id="442d9-124">Vos rapports d’erreurs peuvent aider à améliorer les versions ultérieures du compilateur.</span><span class="sxs-lookup"><span data-stu-id="442d9-124">Your error reports can help improve future compiler releases.</span></span>

 <span data-ttu-id="442d9-125">La capacité d’un utilisateur à envoyer des rapports dépend des autorisations de stratégie ordinateur et utilisateur.</span><span class="sxs-lookup"><span data-stu-id="442d9-125">A user's ability to send reports depends on computer and user policy permissions.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="442d9-126">Pour définir cette option du compilateur dans l'environnement de développement Visual Studio</span><span class="sxs-lookup"><span data-stu-id="442d9-126">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="442d9-127">Ouvrez la page **Propriétés** du projet.</span><span class="sxs-lookup"><span data-stu-id="442d9-127">Open the project's **Properties** page.</span></span> <span data-ttu-id="442d9-128">Pour plus d’informations, consultez [Générer, page du Concepteur de projets (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="442d9-128">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>

2. <span data-ttu-id="442d9-129">Cliquez sur la page de propriétés **Générer**.</span><span class="sxs-lookup"><span data-stu-id="442d9-129">Click the **Build** property page.</span></span>

3. <span data-ttu-id="442d9-130">Cliquez sur le bouton **Avancé**.</span><span class="sxs-lookup"><span data-stu-id="442d9-130">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="442d9-131">Modifiez la propriété **Rapport d’erreurs du compilateur interne**.</span><span class="sxs-lookup"><span data-stu-id="442d9-131">Modify the **Internal Compiler Error Reporting** property.</span></span>

 <span data-ttu-id="442d9-132">Pour plus d'informations sur la façon de définir cette option du compilateur par programme, consultez <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span><span class="sxs-lookup"><span data-stu-id="442d9-132">For information about how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="442d9-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="442d9-133">See also</span></span>

- [<span data-ttu-id="442d9-134">Options de compilateur C</span><span class="sxs-lookup"><span data-stu-id="442d9-134">C# Compiler Options</span></span>](./index.md)
