---
title: Contrôle de l'enregistrement .NET Framework
description: Utilisez le suivi d’événements pour Windows (ETW) pour contrôler les événements de journalisation .NET et d’enregistrement common language runtime (CLR). Utilisez des outils tels que logman, Tracerpt et Xperf.
ms.date: 03/30/2017
helpviewer_keywords:
- CLR ETW events, logging
ms.assetid: ce13088e-3095-4f0e-9f6b-fad30bbd3d41
ms.openlocfilehash: 45d9244eb11b914fd203f24057e1b65c6bef18c2
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309584"
---
# <a name="controlling-net-framework-logging"></a><span data-ttu-id="81bef-104">Contrôle de l'enregistrement .NET Framework</span><span class="sxs-lookup"><span data-stu-id="81bef-104">Controlling .NET Framework Logging</span></span>

<span data-ttu-id="81bef-105">Vous pouvez utiliser le suivi d'événements pour Windows (ETW) pour enregistrer les événements du Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="81bef-105">You can use event tracing for Windows (ETW) to record common language runtime (CLR) events.</span></span> <span data-ttu-id="81bef-106">Vous pouvez créer et afficher des traces à l'aide des outils suivants :</span><span class="sxs-lookup"><span data-stu-id="81bef-106">You can create and view traces by using the following tools:</span></span>

- <span data-ttu-id="81bef-107">Outils en ligne de commande [Logman](/windows-server/administration/windows-commands/logman) et [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) qui sont inclus dans le système d’exploitation Windows.</span><span class="sxs-lookup"><span data-stu-id="81bef-107">The [Logman](/windows-server/administration/windows-commands/logman) and [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) command-line tools, which are included with the Windows operating system.</span></span>

- <span data-ttu-id="81bef-108">Outils en ligne de commande [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) du [Windows Performance Toolkit](/windows-hardware/test/wpt/).</span><span class="sxs-lookup"><span data-stu-id="81bef-108">The [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) tools in the [Windows Performance Toolkit](/windows-hardware/test/wpt/).</span></span> <span data-ttu-id="81bef-109">Pour plus d’informations sur Xperf, consultez le [blog des performances de Windows](https://docs.microsoft.com/archive/blogs/pigscanfly/).</span><span class="sxs-lookup"><span data-stu-id="81bef-109">For more information about Xperf, see the [Windows Performance blog](https://docs.microsoft.com/archive/blogs/pigscanfly/).</span></span>

<span data-ttu-id="81bef-110">Pour capturer des informations sur les événements du CLR, le fournisseur du CLR doit être installé sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="81bef-110">To capture CLR event information, the CLR provider must be installed on your computer.</span></span> <span data-ttu-id="81bef-111">Pour confirmer que le fournisseur est bien installé, tapez `logman query providers` à l'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="81bef-111">To confirm that the provider is installed, type `logman query providers` at the command prompt.</span></span> <span data-ttu-id="81bef-112">La liste des fournisseurs est affichée.</span><span class="sxs-lookup"><span data-stu-id="81bef-112">A list of providers is displayed.</span></span> <span data-ttu-id="81bef-113">Cette liste doit contenir une entrée pour le fournisseur du CLR, comme suit.</span><span class="sxs-lookup"><span data-stu-id="81bef-113">This list should contain an entry for the CLR provider, as follows.</span></span>

```output
Provider                                 GUID
-------------------------------------------------------------------------------
.NET Common Language Runtime    {E13C0D23-CCBC-4E12-931B-D9CC2EEE27E4}.
```

<span data-ttu-id="81bef-114">Si le fournisseur du CLR n’apparaît pas dans la liste, vous pouvez l’installer sur Windows Vista et les systèmes d’exploitation ultérieurs à l’aide de l’outil en ligne de commande Windows [Wevtutil](/windows-server/administration/windows-commands/wevtutil).</span><span class="sxs-lookup"><span data-stu-id="81bef-114">If the CLR provider is not listed, you can install it on Windows Vista and later operating systems by using the Windows [Wevtutil](/windows-server/administration/windows-commands/wevtutil) command-line tool.</span></span> <span data-ttu-id="81bef-115">Ouvrez la fenêtre d’invite de commandes en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="81bef-115">Open the Command Prompt window as an administrator.</span></span> <span data-ttu-id="81bef-116">Remplacez le répertoire de l’invite par le dossier .NET Framework 4 (%WINDIR%\Microsoft.NET\Framework [64] \v4. \<.NET version> \ ).</span><span class="sxs-lookup"><span data-stu-id="81bef-116">Change the prompt directory to the .NET Framework 4 folder (%WINDIR%\Microsoft.NET\Framework[64]\v4.\<.NET version>\ ).</span></span> <span data-ttu-id="81bef-117">Ce dossier contient le fichier ETW.man du CLR.</span><span class="sxs-lookup"><span data-stu-id="81bef-117">This folder contains the CLR-ETW.man file.</span></span> <span data-ttu-id="81bef-118">À l'invite de commandes, tapez la commande suivante pour installer le fournisseur du CLR.</span><span class="sxs-lookup"><span data-stu-id="81bef-118">At the command prompt, type the following command to install the CLR provider:</span></span>

`wevtutil im CLR-ETW.man`

## <a name="capturing-clr-etw-events"></a><span data-ttu-id="81bef-119">Capture des événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="81bef-119">Capturing CLR ETW Events</span></span>

<span data-ttu-id="81bef-120">Vous pouvez utiliser les outils en ligne de commande [Logman](/windows-server/administration/windows-commands/logman) et [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) pour capturer des événements ETW, et les outils [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) et [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) pour décoder les événements Trace.</span><span class="sxs-lookup"><span data-stu-id="81bef-120">You can use the [Logman](/windows-server/administration/windows-commands/logman) and [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) command-line tools to capture ETW events, and the [Tracerpt](/windows-server/administration/windows-commands/tracerpt_1) and [Xperf](/windows-hardware/test/wpt/xperf-command-line-reference) tools to decode the trace events.</span></span>

<span data-ttu-id="81bef-121">Pour activer la journalisation, un utilisateur doit spécifier trois éléments :</span><span class="sxs-lookup"><span data-stu-id="81bef-121">To turn on logging, a user must specify three things:</span></span>

- <span data-ttu-id="81bef-122">Le fournisseur vers lequel communiquer.</span><span class="sxs-lookup"><span data-stu-id="81bef-122">The provider to communicate to.</span></span>

- <span data-ttu-id="81bef-123">Un nombre 64 bits qui représente un jeu de mots clés.</span><span class="sxs-lookup"><span data-stu-id="81bef-123">A 64-bit number that represents a set of keywords.</span></span> <span data-ttu-id="81bef-124">Chaque mot clé représente un jeu d'événements que le fournisseur peut activer.</span><span class="sxs-lookup"><span data-stu-id="81bef-124">Each keyword represents a set of events that the provider can turn on.</span></span> <span data-ttu-id="81bef-125">Le nombre représente un jeu combiné de mots clés à activer.</span><span class="sxs-lookup"><span data-stu-id="81bef-125">The number represents a combined set of keywords to turn on.</span></span>

- <span data-ttu-id="81bef-126">Un petit nombre représentant le niveau (commentaires) à journaliser.</span><span class="sxs-lookup"><span data-stu-id="81bef-126">A small number representing the level (verbosity) to log at.</span></span> <span data-ttu-id="81bef-127">Le niveau 1 est le moins détaillé, et le niveau 5 est le plus détaillé.</span><span class="sxs-lookup"><span data-stu-id="81bef-127">Level 1 is the least verbose, and level 5 is the most verbose.</span></span> <span data-ttu-id="81bef-128">Le niveau 0 est une valeur par défaut dont la signification est spécifique au fournisseur.</span><span class="sxs-lookup"><span data-stu-id="81bef-128">Level 0 is a default whose meaning is provider-specific.</span></span>

### <a name="to-capture-clr-etw-events-using-logman"></a><span data-ttu-id="81bef-129">Pour capturer les événements ETW du CLR à l'aide de Logman</span><span class="sxs-lookup"><span data-stu-id="81bef-129">To capture CLR ETW events using Logman</span></span>

1. <span data-ttu-id="81bef-130">À l’invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="81bef-130">At the command prompt, type:</span></span>

     `logman start clrevents -p {e13c0d23-ccbc-4e12-931b-d9cc2eee27e4} 0x1CCBD 0x5 -ets -ct perf`

     <span data-ttu-id="81bef-131">où :</span><span class="sxs-lookup"><span data-stu-id="81bef-131">where:</span></span>

    - <span data-ttu-id="81bef-132">Le paramètre `-p` identifie le GUID du fournisseur.</span><span class="sxs-lookup"><span data-stu-id="81bef-132">The `-p` parameter identifies the provider GUID.</span></span>

    - <span data-ttu-id="81bef-133">`0x1CCBD` spécifie les catégories d'événements qui seront déclenchés.</span><span class="sxs-lookup"><span data-stu-id="81bef-133">`0x1CCBD` specifies the categories of events that will be raised.</span></span>

    - <span data-ttu-id="81bef-134">`0x5` définit le niveau de la journalisation (dans ce cas, détaillé (5)).</span><span class="sxs-lookup"><span data-stu-id="81bef-134">`0x5` sets the level of logging (in this case, verbose (5)).</span></span>

    - <span data-ttu-id="81bef-135">Le paramètre `-ets` indique à Logman d'envoyer des commandes aux sessions de suivi d'événements.</span><span class="sxs-lookup"><span data-stu-id="81bef-135">The `-ets` parameter instructs Logman to send commands to event tracing sessions.</span></span>

    - <span data-ttu-id="81bef-136">Le paramètre `-ct perf` indique que la fonction `QueryPerformanceCounter` sera utilisée pour enregistrer l'horodatage de chaque événement.</span><span class="sxs-lookup"><span data-stu-id="81bef-136">The `-ct perf` parameter specifies that the `QueryPerformanceCounter` function will be used to log the time stamp for each event.</span></span>

2. <span data-ttu-id="81bef-137">Pour arrêter de journaliser les événements, tapez :</span><span class="sxs-lookup"><span data-stu-id="81bef-137">To stop logging the events, type:</span></span>

     `logman stop clrevents -ets`

     <span data-ttu-id="81bef-138">Cette commande crée un fichier de suivi binaire nommé clrevents.etl.</span><span class="sxs-lookup"><span data-stu-id="81bef-138">This command creates a binary trace file named clrevents.etl.</span></span>

### <a name="to-capture-clr-etw-events-using-xperf"></a><span data-ttu-id="81bef-139">Pour capturer les événements ETW du CLR à l’aide de Xperf</span><span class="sxs-lookup"><span data-stu-id="81bef-139">To capture CLR ETW events using Xperf</span></span>

1. <span data-ttu-id="81bef-140">À l’invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="81bef-140">At the command prompt, type:</span></span>

     `xperf -start clr -on e13c0d23-ccbc-4e12-931b-d9cc2eee27e4:0x1CCBD:5 -f clrevents.etl`

     <span data-ttu-id="81bef-141">où le GUID est le GUID du fournisseur ETW du CLR et `0x1CCBD:5` effectue le suivi de tous les éléments de niveaux 5 (détaillé) et inférieurs.</span><span class="sxs-lookup"><span data-stu-id="81bef-141">where the GUID is the CLR ETW provider GUID, and `0x1CCBD:5` traces everything at and below level 5 (verbose).</span></span>

2. <span data-ttu-id="81bef-142">Pour arrêter le suivi, tapez :</span><span class="sxs-lookup"><span data-stu-id="81bef-142">To stop tracing, type:</span></span>

     `Xperf -stop clr`

     <span data-ttu-id="81bef-143">Cette commande crée un fichier de suivi nommé clrevents.etl.</span><span class="sxs-lookup"><span data-stu-id="81bef-143">This command creates a trace file named clrevents.etl.</span></span>

## <a name="viewing-clr-etw-events"></a><span data-ttu-id="81bef-144">Affichage des événements ETW du CLR</span><span class="sxs-lookup"><span data-stu-id="81bef-144">Viewing CLR ETW Events</span></span>

<span data-ttu-id="81bef-145">Utilisez les commandes répertoriées ci-dessous pour afficher les événements ETW du CLR.</span><span class="sxs-lookup"><span data-stu-id="81bef-145">Use the commands listed below to view the CLR ETW events.</span></span> <span data-ttu-id="81bef-146">Pour obtenir une description des événements, consultez [Événements ETW du CLR](clr-etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="81bef-146">For a description of the events, see [CLR ETW Events](clr-etw-events.md).</span></span>

### <a name="to-view-clr-etw-events-using-tracerpt"></a><span data-ttu-id="81bef-147">Pour afficher les événements ETW du CLR à l'aide de Tracerpt</span><span class="sxs-lookup"><span data-stu-id="81bef-147">To view CLR ETW events using Tracerpt</span></span>

- <span data-ttu-id="81bef-148">À l’invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="81bef-148">At the command prompt, type:</span></span>

     `tracerpt clrevents.etl`

     <span data-ttu-id="81bef-149">Cette commande crée deux fichiers : dumpfile.xml et summary.txt.</span><span class="sxs-lookup"><span data-stu-id="81bef-149">This command creates two files: dumpfile.xml and summary.txt.</span></span> <span data-ttu-id="81bef-150">Le fichier dumpfile.xml répertorie tous les événements et le fichier summary.txt fournit un résumé des événements.</span><span class="sxs-lookup"><span data-stu-id="81bef-150">The dumpfile.xml file lists all the events, and summary.txt provides a summary of the events.</span></span>

### <a name="to-view-clr-etw-events-using-xperf"></a><span data-ttu-id="81bef-151">Pour afficher les événements ETW du CLR à l’aide de Xperf</span><span class="sxs-lookup"><span data-stu-id="81bef-151">To view CLR ETW events using Xperf</span></span>

- <span data-ttu-id="81bef-152">À l’invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="81bef-152">At the command prompt, type:</span></span>

     `xperf clrevents.etl`

     <span data-ttu-id="81bef-153">Cette commande ouvre la visionneuse de fichiers ETL de Xperf.</span><span class="sxs-lookup"><span data-stu-id="81bef-153">This command opens the Xperf ETL file viewer.</span></span> <span data-ttu-id="81bef-154">Dans cette visionneuse, les événements CLR s’affichent dans la vue **Événements génériques**.</span><span class="sxs-lookup"><span data-stu-id="81bef-154">In this viewer, the CLR events show up in the **Generic Events** view.</span></span> <span data-ttu-id="81bef-155">Pour afficher une grille de données d’événements catégorisée par type, sélectionnez une plage horaire dans cette vue, puis cliquez avec le bouton droit et sélectionnez **Résumé**.</span><span class="sxs-lookup"><span data-stu-id="81bef-155">To display a data grid of events categorized by type, select a region of time in this view, and then right-click and select **Summary**.</span></span>

### <a name="to-convert-the-etl-file-to-a-comma-separated-value-file"></a><span data-ttu-id="81bef-156">Pour convertir le fichier .etl en fichier .csv</span><span class="sxs-lookup"><span data-stu-id="81bef-156">To convert the .etl file to a comma-separated value file</span></span>

- <span data-ttu-id="81bef-157">À l’invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="81bef-157">At the command prompt, type:</span></span>

     `xperf -i clrevents.etl -f clrevents.csv`

     <span data-ttu-id="81bef-158">Cette commande indique à Xperf d’effectuer un dump des événements dans un fichier de valeurs séparées par des virgules (.csv) que vous pouvez consulter.</span><span class="sxs-lookup"><span data-stu-id="81bef-158">This command causes XPerf to dump the events as a comma separated value (CSV) file that you can view.</span></span> <span data-ttu-id="81bef-159">Étant donné que des événements différents ont des champs différents, ce fichier .csv contient plusieurs lignes d'en-têtes avant les données.</span><span class="sxs-lookup"><span data-stu-id="81bef-159">Because different events have different fields, this CSV file is contains more than one header line before the data.</span></span> <span data-ttu-id="81bef-160">Le premier champ de chaque ligne correspond au type d'événement, qui indique l'en-tête à utiliser pour déterminer le reste des champs.</span><span class="sxs-lookup"><span data-stu-id="81bef-160">The first field of every line is the event type, which indicates which header should be used to determine the rest of the fields.</span></span>

## <a name="see-also"></a><span data-ttu-id="81bef-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81bef-161">See also</span></span>

- [<span data-ttu-id="81bef-162">Windows Performance Toolkit</span><span class="sxs-lookup"><span data-stu-id="81bef-162">Windows Performance Toolkit</span></span>](/windows-hardware/test/wpt/)
- [<span data-ttu-id="81bef-163">Événements ETW dans le Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="81bef-163">ETW Events in the Common Language Runtime</span></span>](etw-events-in-the-common-language-runtime.md)
