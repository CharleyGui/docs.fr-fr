---
title: Clrver.exe (outil CLR Version)
description: Passez en revue Clrver.exe, l’outil CLR version. Cet outil signale toutes les versions installées du common language runtime (CLR) sur l’ordinateur.
ms.date: 03/30/2017
helpviewer_keywords:
- Clrver.exe
- CLR Version tool
ms.assetid: cbc2ee86-bdc8-4a65-a8f1-ba23bce3a699
ms.openlocfilehash: 3a7a585d990051553aa8fdc0e99b2dc206273cf4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247224"
---
# <a name="clrverexe-clr-version-tool"></a><span data-ttu-id="40f58-104">Clrver.exe (outil CLR Version)</span><span class="sxs-lookup"><span data-stu-id="40f58-104">Clrver.exe (CLR Version Tool)</span></span>

<span data-ttu-id="40f58-105">L'outil de version CLR (Clrver.exe) rapporte toutes les versions installées du CLR (Common Runtime Language) sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="40f58-105">The CLR Version tool (Clrver.exe) reports all the installed versions of the common language runtime (CLR) on the computer.</span></span>  
  
 <span data-ttu-id="40f58-106">Cet outil est installé automatiquement avec Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="40f58-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="40f58-107">Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7).</span><span class="sxs-lookup"><span data-stu-id="40f58-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="40f58-108">Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="40f58-108">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="40f58-109">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="40f58-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40f58-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40f58-110">Syntax</span></span>  
  
```console  
clrver [option]  
```  
  
## <a name="options"></a><span data-ttu-id="40f58-111">Options</span><span class="sxs-lookup"><span data-stu-id="40f58-111">Options</span></span>  
  
|<span data-ttu-id="40f58-112">Option</span><span class="sxs-lookup"><span data-stu-id="40f58-112">Option</span></span>|<span data-ttu-id="40f58-113">Description</span><span class="sxs-lookup"><span data-stu-id="40f58-113">Description</span></span>|  
|------------|-----------------|  
|`-all`|<span data-ttu-id="40f58-114">Affiche tous les processus de l'ordinateur qui utilisent le CLR.</span><span class="sxs-lookup"><span data-stu-id="40f58-114">Displays all processes on the computer that are using the CLR.</span></span>|  
|<span data-ttu-id="40f58-115">*ELECTRIQUE*</span><span class="sxs-lookup"><span data-stu-id="40f58-115">*pid*</span></span>|<span data-ttu-id="40f58-116">Affiche la ou les versions du CLR utilisé par le processus qui a l'ID de processus spécifié (PID).</span><span class="sxs-lookup"><span data-stu-id="40f58-116">Displays the version(s) of the CLR used by the process that has the specified process ID (PID).</span></span>|  
|`-?`|<span data-ttu-id="40f58-117">Affiche la syntaxe et les options de commande de l'outil.</span><span class="sxs-lookup"><span data-stu-id="40f58-117">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40f58-118">Notes</span><span class="sxs-lookup"><span data-stu-id="40f58-118">Remarks</span></span>  

 <span data-ttu-id="40f58-119">Si vous appelez Clrver.exe sans option, il affiche toutes les versions de CLR installées.</span><span class="sxs-lookup"><span data-stu-id="40f58-119">If you call Clrver.exe with no options, it displays all installed CLR versions.</span></span> <span data-ttu-id="40f58-120">Si vous spécifiez PID pour un autre utilisateur, vous devez disposer des autorisations d'administrateur pour obtenir les informations de version.</span><span class="sxs-lookup"><span data-stu-id="40f58-120">If you specify a PID for another user, you must have administrative permissions to obtain the version information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40f58-121">Dans Windows Vista et version ultérieure, le contrôle de compte d'utilisateur détermine les privilèges d'un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="40f58-121">In Windows Vista and later, User Account Control (UAC) determines the privileges of a user.</span></span> <span data-ttu-id="40f58-122">Si vous êtes membre du groupe Administrateurs intégrés, deux jetons d'accès au moment de l'exécution vous sont assignés : un jeton d'accès utilisateur standard et un jeton d'accès administrateur.</span><span class="sxs-lookup"><span data-stu-id="40f58-122">If you are a member of the Built-in Administrators group, you are assigned two run-time access tokens: a standard user access token and an administrator access token.</span></span> <span data-ttu-id="40f58-123">Par défaut, vous êtes dans le rôle d'utilisateur standard.</span><span class="sxs-lookup"><span data-stu-id="40f58-123">By default, you are in the standard user role.</span></span> <span data-ttu-id="40f58-124">Pour exécuter le code qui requiert une autorisation d'administration, vous devez d'abord élever vos privilèges d'utilisateur standard à administrateur.</span><span class="sxs-lookup"><span data-stu-id="40f58-124">To execute code that requires administrative permission, you must first elevate your privileges from standard user to administrator.</span></span> <span data-ttu-id="40f58-125">Cela peut être effectué au démarrage de l'invite de commandes en cliquant avec le bouton droit sur l'icône de l'invite de commandes et en indiquant que vous voulez l'exécuter en tant qu'administrateur.</span><span class="sxs-lookup"><span data-stu-id="40f58-125">You can do this when you start the command prompt by right-clicking the command prompt icon and indicating that you want to run as an administrator.</span></span>  
  
 <span data-ttu-id="40f58-126">La tentative afin de déterminer la version du CLR pour des processus SYSTÈME, SERVICE LOCAL et SERVICE RÉSEAU entraîne un message indiquant que le PID n'existe pas.</span><span class="sxs-lookup"><span data-stu-id="40f58-126">Attempting to determine the CLR version for SYSTEM, LOCAL SERVICE, and NETWORK SERVICE processes results in a message indicating that the PID doesn't exist.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="40f58-127">Exemples</span><span class="sxs-lookup"><span data-stu-id="40f58-127">Examples</span></span>  

 <span data-ttu-id="40f58-128">La commande suivante affiche toutes les versions du CLR installée sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="40f58-128">The following command displays all the versions of the CLR installed on the computer.</span></span>  
  
 `clrver`  
  
 <span data-ttu-id="40f58-129">La commande suivante affiche la version du CLR utilisée par le processus 128.</span><span class="sxs-lookup"><span data-stu-id="40f58-129">The following command displays the version of the CLR used by process 128.</span></span>  
  
 `clrver 128`  
  
 <span data-ttu-id="40f58-130">La commande suivante affiche tous les processus gérés et la version du CLR qu'ils utilisent.</span><span class="sxs-lookup"><span data-stu-id="40f58-130">The following command displays all the managed processes and the version of the CLR they are using.</span></span>  
  
 `Clrver -all`  
  
## <a name="see-also"></a><span data-ttu-id="40f58-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40f58-131">See also</span></span>

- [<span data-ttu-id="40f58-132">outils</span><span class="sxs-lookup"><span data-stu-id="40f58-132">Tools</span></span>](index.md)
- [<span data-ttu-id="40f58-133">Invites de commandes</span><span class="sxs-lookup"><span data-stu-id="40f58-133">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
