---
title: Contrôle de l'enregistrement .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events, logging
ms.assetid: ce13088e-3095-4f0e-9f6b-fad30bbd3d41
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 29f6f844c3cdf2d43437aed7fc19492a37f9f8fc
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971565"
---
# <a name="controlling-net-framework-logging"></a><span data-ttu-id="37f49-102">Contrôle de l'enregistrement .NET Framework</span><span class="sxs-lookup"><span data-stu-id="37f49-102">Controlling .NET Framework Logging</span></span>

<span data-ttu-id="37f49-103">Vous pouvez utiliser le suivi d'événements pour Windows (ETW) pour enregistrer les événements du Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="37f49-103">You can use event tracing for Windows (ETW) to record common language runtime (CLR) events.</span></span> <span data-ttu-id="37f49-104">Vous pouvez créer et afficher des traces à l'aide des outils suivants :</span><span class="sxs-lookup"><span data-stu-id="37f49-104">You can create and view traces by using the following tools:</span></span>

- <span data-ttu-id="37f49-105">Outils en ligne de commande [Logman](/windows-server/administration/windows-commands/logman) et [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) qui sont inclus dans le système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="37f49-105">The [Logman](/windows-server/administration/windows-commands/logman) and [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) command-line tools, which are included with the Windows operating system.</span></span>

- <span data-ttu-id="37f49-106">Outils en ligne de commande [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) du [Windows Performance Toolkit](/windows-hardware/test/wpt/).</span><span class="sxs-lookup"><span data-stu-id="37f49-106">The [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) tools in the [Windows Performance Toolkit](/windows-hardware/test/wpt/).</span></span> <span data-ttu-id="37f49-107">Pour plus d’informations sur Xperf, consultez le [blog des performances de Windows](https://go.microsoft.com/fwlink/?LinkId=179509).</span><span class="sxs-lookup"><span data-stu-id="37f49-107">For more information about Xperf, see the [Windows Performance blog](https://go.microsoft.com/fwlink/?LinkId=179509).</span></span>

<span data-ttu-id="37f49-108">Pour capturer des informations sur les événements du CLR, le fournisseur du CLR doit être installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="37f49-108">To capture CLR event information, the CLR provider must be installed on your computer.</span></span> <span data-ttu-id="37f49-109">Pour confirmer que le fournisseur est bien installé, tapez `logman query providers` à l'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="37f49-109">To confirm that the provider is installed, type `logman query providers` at the command prompt.</span></span> <span data-ttu-id="37f49-110">La liste des fournisseurs est affichée.</span><span class="sxs-lookup"><span data-stu-id="37f49-110">A list of providers is displayed.</span></span> <span data-ttu-id="37f49-111">Cette liste doit contenir une entrée pour le fournisseur du CLR, comme suit.</span><span class="sxs-lookup"><span data-stu-id="37f49-111">This list should contain an entry for the CLR provider, as follows.</span></span>

```
Provider                                 GUID
-------------------------------------------------------------------------------
.NET Common Language Runtime    {E13C0D23-CCBC-4E12-931B-D9CC2EEE27E4}.
```

<span data-ttu-id="37f49-112">Si le fournisseur du CLR n’apparaît pas dans la liste, vous pouvez l’installer sur Windows Vista et les systèmes d’exploitation ultérieurs à l’aide de l’outil en ligne de commande Windows [Wevtutil](/windows-server/administration/windows-commands/wevtutil).</span><span class="sxs-lookup"><span data-stu-id="37f49-112">If the CLR provider is not listed, you can install it on Windows Vista and later operating systems by using the Windows [Wevtutil](/windows-server/administration/windows-commands/wevtutil) command-line tool.</span></span> <span data-ttu-id="37f49-113">Ouvrez la fenêtre d’invite de commandes en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="37f49-113">Open the Command Prompt window as an administrator.</span></span> <span data-ttu-id="37f49-114">Remplacez le répertoire de l’invite par le dossier .NET Framework 4 (%WINDIR%\Microsoft.NET\Framework [64\<] \v4. NET version > \).</span><span class="sxs-lookup"><span data-stu-id="37f49-114">Change the prompt directory to the .NET Framework 4 folder (%WINDIR%\Microsoft.NET\Framework[64]\v4.\<.NET version>\ ).</span></span> <span data-ttu-id="37f49-115">Ce dossier contient le fichier ETW.man du CLR.</span><span class="sxs-lookup"><span data-stu-id="37f49-115">This folder contains the CLR-ETW.man file.</span></span> <span data-ttu-id="37f49-116">À l'invite de commandes, tapez la commande suivante pour installer le fournisseur du CLR.</span><span class="sxs-lookup"><span data-stu-id="37f49-116">At the command prompt, type the following command to install the CLR provider:</span></span>

`wevtutil im CLR-ETW.man`

## <a name="capturing-clr-etw-events"></a><span data-ttu-id="37f49-117">Capture des événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="37f49-117">Capturing CLR ETW Events</span></span>

<span data-ttu-id="37f49-118">Vous pouvez utiliser les outils en ligne de commande [Logman](/windows-server/administration/windows-commands/logman) et [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) pour capturer des événements ETW, et les outils [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) et [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) pour décoder les événements Trace.</span><span class="sxs-lookup"><span data-stu-id="37f49-118">You can use the [Logman](/windows-server/administration/windows-commands/logman) and [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) command-line tools to capture ETW events, and the [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) and [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) tools to decode the trace events.</span></span>

<span data-ttu-id="37f49-119">Pour activer la journalisation, un utilisateur doit spécifier trois éléments :</span><span class="sxs-lookup"><span data-stu-id="37f49-119">To turn on logging, a user must specify three things:</span></span>

- <span data-ttu-id="37f49-120">Le fournisseur vers lequel communiquer.</span><span class="sxs-lookup"><span data-stu-id="37f49-120">The provider to communicate to.</span></span>

- <span data-ttu-id="37f49-121">Un nombre 64 bits qui représente un jeu de mots clés.</span><span class="sxs-lookup"><span data-stu-id="37f49-121">A 64-bit number that represents a set of keywords.</span></span> <span data-ttu-id="37f49-122">Chaque mot clé représente un jeu d'événements que le fournisseur peut activer.</span><span class="sxs-lookup"><span data-stu-id="37f49-122">Each keyword represents a set of events that the provider can turn on.</span></span> <span data-ttu-id="37f49-123">Le nombre représente un jeu combiné de mots clés à activer.</span><span class="sxs-lookup"><span data-stu-id="37f49-123">The number represents a combined set of keywords to turn on.</span></span>

- <span data-ttu-id="37f49-124">Un petit nombre représentant le niveau (commentaires) à journaliser.</span><span class="sxs-lookup"><span data-stu-id="37f49-124">A small number representing the level (verbosity) to log at.</span></span> <span data-ttu-id="37f49-125">Le niveau 1 est le moins détaillé, et le niveau 5 est le plus détaillé.</span><span class="sxs-lookup"><span data-stu-id="37f49-125">Level 1 is the least verbose, and level 5 is the most verbose.</span></span> <span data-ttu-id="37f49-126">Le niveau 0 est une valeur par défaut dont la signification est spécifique au fournisseur.</span><span class="sxs-lookup"><span data-stu-id="37f49-126">Level 0 is a default whose meaning is provider-specific.</span></span>

### <a name="to-capture-clr-etw-events-using-logman"></a><span data-ttu-id="37f49-127">Pour capturer les événements ETW du CLR à l'aide de Logman</span><span class="sxs-lookup"><span data-stu-id="37f49-127">To capture CLR ETW events using Logman</span></span>

1. <span data-ttu-id="37f49-128">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="37f49-128">At the command prompt, type:</span></span>

     `logman start clrevents -p {e13c0d23-ccbc-4e12-931b-d9cc2eee27e4} 0x1CCBD 0x5 -ets -ct perf`

     <span data-ttu-id="37f49-129">où :</span><span class="sxs-lookup"><span data-stu-id="37f49-129">where:</span></span>

    - <span data-ttu-id="37f49-130">Le paramètre `-p` identifie le GUID du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="37f49-130">The `-p` parameter identifies the provider GUID.</span></span>

    - <span data-ttu-id="37f49-131">`0x1CCBD` spécifie les catégories d'événements qui seront déclenchés.</span><span class="sxs-lookup"><span data-stu-id="37f49-131">`0x1CCBD` specifies the categories of events that will be raised.</span></span>

    - <span data-ttu-id="37f49-132">`0x5` définit le niveau de la journalisation (dans ce cas, détaillé (5)).</span><span class="sxs-lookup"><span data-stu-id="37f49-132">`0x5` sets the level of logging (in this case, verbose (5)).</span></span>

    - <span data-ttu-id="37f49-133">Le paramètre `-ets` indique à Logman d'envoyer des commandes aux sessions de suivi d'événements.</span><span class="sxs-lookup"><span data-stu-id="37f49-133">The `-ets` parameter instructs Logman to send commands to event tracing sessions.</span></span>

    - <span data-ttu-id="37f49-134">Le paramètre `-ct perf` indique que la fonction `QueryPerformanceCounter` sera utilisée pour enregistrer l'horodatage de chaque événement.</span><span class="sxs-lookup"><span data-stu-id="37f49-134">The `-ct perf` parameter specifies that the `QueryPerformanceCounter` function will be used to log the time stamp for each event.</span></span>

2. <span data-ttu-id="37f49-135">Pour arrêter de journaliser les événements, tapez :</span><span class="sxs-lookup"><span data-stu-id="37f49-135">To stop logging the events, type:</span></span>

     `logman stop clrevents -ets`

     <span data-ttu-id="37f49-136">Cette commande crée un fichier de suivi binaire nommé clrevents.etl.</span><span class="sxs-lookup"><span data-stu-id="37f49-136">This command creates a binary trace file named clrevents.etl.</span></span>

### <a name="to-capture-clr-etw-events-using-xperf"></a><span data-ttu-id="37f49-137">Pour capturer les événements ETW du CLR à l’aide de Xperf</span><span class="sxs-lookup"><span data-stu-id="37f49-137">To capture CLR ETW events using Xperf</span></span>

1. <span data-ttu-id="37f49-138">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="37f49-138">At the command prompt, type:</span></span>

     `xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:5 -f clrevents.etl`

     <span data-ttu-id="37f49-139">où le GUID est le GUID du fournisseur ETW du CLR et `0x1CCBD:5` effectue le suivi de tous les éléments de niveaux 5 (détaillé) et inférieurs.</span><span class="sxs-lookup"><span data-stu-id="37f49-139">where the GUID is the CLR ETW provider GUID, and `0x1CCBD:5` traces everything at and below level 5 (verbose).</span></span>

2. <span data-ttu-id="37f49-140">Pour arrêter le suivi, tapez :</span><span class="sxs-lookup"><span data-stu-id="37f49-140">To stop tracing, type:</span></span>

     `Xperf -stop clr`

     <span data-ttu-id="37f49-141">Cette commande crée un fichier de suivi nommé clrevents.etl.</span><span class="sxs-lookup"><span data-stu-id="37f49-141">This command creates a trace file named clrevents.etl.</span></span>

## <a name="viewing-clr-etw-events"></a><span data-ttu-id="37f49-142">Affichage des événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="37f49-142">Viewing CLR ETW Events</span></span>

<span data-ttu-id="37f49-143">Utilisez les commandes répertoriées ci-dessous pour afficher les événements ETW du CLR.</span><span class="sxs-lookup"><span data-stu-id="37f49-143">Use the commands listed below to view the CLR ETW events.</span></span> <span data-ttu-id="37f49-144">Pour obtenir une description des événements, consultez [Événements ETW du CLR](../../../docs/framework/performance/clr-etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="37f49-144">For a description of the events, see [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md).</span></span>

### <a name="to-view-clr-etw-events-using-tracerpt"></a><span data-ttu-id="37f49-145">Pour afficher les événements ETW du CLR à l'aide de Tracerpt</span><span class="sxs-lookup"><span data-stu-id="37f49-145">To view CLR ETW events using Tracerpt</span></span>

- <span data-ttu-id="37f49-146">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="37f49-146">At the command prompt, type:</span></span>

     `tracerpt clrevents.etl`

     <span data-ttu-id="37f49-147">Cette commande crée deux fichiers : dumpfile.xml et summary.txt.</span><span class="sxs-lookup"><span data-stu-id="37f49-147">This command creates two files: dumpfile.xml and summary.txt.</span></span> <span data-ttu-id="37f49-148">Le fichier dumpfile.xml répertorie tous les événements et le fichier summary.txt fournit un résumé des événements.</span><span class="sxs-lookup"><span data-stu-id="37f49-148">The dumpfile.xml file lists all the events, and summary.txt provides a summary of the events.</span></span>

### <a name="to-view-clr-etw-events-using-xperf"></a><span data-ttu-id="37f49-149">Pour afficher les événements ETW du CLR à l’aide de Xperf</span><span class="sxs-lookup"><span data-stu-id="37f49-149">To view CLR ETW events using Xperf</span></span>

- <span data-ttu-id="37f49-150">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="37f49-150">At the command prompt, type:</span></span>

     `xperf clrevents.etl`

     <span data-ttu-id="37f49-151">Cette commande ouvre la visionneuse de fichiers ETL de Xperf.</span><span class="sxs-lookup"><span data-stu-id="37f49-151">This command opens the Xperf ETL file viewer.</span></span> <span data-ttu-id="37f49-152">Dans cette visionneuse, les événements CLR s’affichent dans la vue **Événements génériques**.</span><span class="sxs-lookup"><span data-stu-id="37f49-152">In this viewer, the CLR events show up in the **Generic Events** view.</span></span> <span data-ttu-id="37f49-153">Pour afficher une grille de données d’événements catégorisée par type, sélectionnez une plage horaire dans cette vue, puis cliquez avec le bouton droit et sélectionnez **Résumé**.</span><span class="sxs-lookup"><span data-stu-id="37f49-153">To display a data grid of events categorized by type, select a region of time in this view, and then right-click and select **Summary**.</span></span>

### <a name="to-convert-the-etl-file-to-a-comma-separated-value-file"></a><span data-ttu-id="37f49-154">Pour convertir le fichier .etl en fichier .csv</span><span class="sxs-lookup"><span data-stu-id="37f49-154">To convert the .etl file to a comma-separated value file</span></span>

- <span data-ttu-id="37f49-155">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="37f49-155">At the command prompt, type:</span></span>

     `xperf -i clrevents.etl -f clrevents.csv`

     <span data-ttu-id="37f49-156">Cette commande indique à Xperf d’effectuer un dump des événements dans un fichier de valeurs séparées par des virgules (.csv) que vous pouvez consulter.</span><span class="sxs-lookup"><span data-stu-id="37f49-156">This command causes XPerf to dump the events as a comma separated value (CSV) file that you can view.</span></span> <span data-ttu-id="37f49-157">Étant donné que des événements différents ont des champs différents, ce fichier .csv contient plusieurs lignes d'en-têtes avant les données.</span><span class="sxs-lookup"><span data-stu-id="37f49-157">Because different events have different fields, this CSV file is contains more than one header line before the data.</span></span> <span data-ttu-id="37f49-158">Le premier champ de chaque ligne correspond au type d'événement, qui indique l'en-tête à utiliser pour déterminer le reste des champs.</span><span class="sxs-lookup"><span data-stu-id="37f49-158">The first field of every line is the event type, which indicates which header should be used to determine the rest of the fields.</span></span>

## <a name="see-also"></a><span data-ttu-id="37f49-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37f49-159">See also</span></span>

- [<span data-ttu-id="37f49-160">Kit de performances Windows</span><span class="sxs-lookup"><span data-stu-id="37f49-160">Windows Performance Toolkit</span></span>](/windows-hardware/test/wpt/)
- [<span data-ttu-id="37f49-161">Événements ETW dans le Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="37f49-161">ETW Events in the Common Language Runtime</span></span>](../../../docs/framework/performance/etw-events-in-the-common-language-runtime.md)
