---
title: 'Procédure : Déboguer les applications prenant en charge les revendications et les services utilisant le suivi WIF'
ms.date: 03/30/2017
ms.assetid: 3d51ba59-3adb-4ca4-bd33-5027531af687
author: BrucePerlerMS
ms.openlocfilehash: effd670a4d0e12f0bca10301fabc361c73e03328
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625879"
---
# <a name="how-to-debug-claims-aware-applications-and-services-using-wif-tracing"></a><span data-ttu-id="26081-102">Procédure : Déboguer les applications prenant en charge les revendications et les services utilisant le suivi WIF</span><span class="sxs-lookup"><span data-stu-id="26081-102">How To: Debug Claims-Aware Applications And Services Using WIF Tracing</span></span>
## <a name="applies-to"></a><span data-ttu-id="26081-103">S'applique à</span><span class="sxs-lookup"><span data-stu-id="26081-103">Applies To</span></span>  
  
- <span data-ttu-id="26081-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="26081-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>  
  
- <span data-ttu-id="26081-105">Service Trace Viewer Tool (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="26081-105">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>  
  
- <span data-ttu-id="26081-106">Dépannage et débogage des applications WIF</span><span class="sxs-lookup"><span data-stu-id="26081-106">Troubleshooting and Debugging WIF Applications</span></span>  
  
## <a name="summary"></a><span data-ttu-id="26081-107">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="26081-107">Summary</span></span>  
 <span data-ttu-id="26081-108">Cette procédure décrit les étapes à suivre pour configurer le suivi WIF, collecter les journaux de suivi et analyser ceux-ci à l'aide de l'outil Trace Viewer.</span><span class="sxs-lookup"><span data-stu-id="26081-108">This How-To describes required steps for how to configure WIF tracing, collect trace logs, and how to analyze the trace logs using Trace Viewer tool.</span></span> <span data-ttu-id="26081-109">Elle établit une correspondance générale entre les entrées de suivi et les mesures nécessaires pour résoudre les problèmes liés à WIF.</span><span class="sxs-lookup"><span data-stu-id="26081-109">It provides general mapping for trace entries to actions needed to troubleshoot issues related to WIF.</span></span>  
  
## <a name="contents"></a><span data-ttu-id="26081-110">Sommaire</span><span class="sxs-lookup"><span data-stu-id="26081-110">Contents</span></span>  
  
- <span data-ttu-id="26081-111">Objectifs</span><span class="sxs-lookup"><span data-stu-id="26081-111">Objectives</span></span>  
  
- <span data-ttu-id="26081-112">Résumé des étapes</span><span class="sxs-lookup"><span data-stu-id="26081-112">Summary of Steps</span></span>  
  
- <span data-ttu-id="26081-113">Étape 1 : configurer le suivi WIF à l'aide du fichier de configuration Web.config</span><span class="sxs-lookup"><span data-stu-id="26081-113">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
  
- <span data-ttu-id="26081-114">Étape 2 : analyser les fichiers de suivi WIF à l'aide de l'outil Trace Viewer</span><span class="sxs-lookup"><span data-stu-id="26081-114">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
  
- <span data-ttu-id="26081-115">Étape 3 : identifier les solutions pour corriger les problèmes liés à WIF</span><span class="sxs-lookup"><span data-stu-id="26081-115">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
  
- <span data-ttu-id="26081-116">Éléments associés</span><span class="sxs-lookup"><span data-stu-id="26081-116">Related Items</span></span>  
  
## <a name="objectives"></a><span data-ttu-id="26081-117">Objectifs</span><span class="sxs-lookup"><span data-stu-id="26081-117">Objectives</span></span>  
  
- <span data-ttu-id="26081-118">Configurer le suivi WIF.</span><span class="sxs-lookup"><span data-stu-id="26081-118">Configure WIF tracing.</span></span>  
  
- <span data-ttu-id="26081-119">Consulter les journaux de suivi dans l'outil Trace Viewer.</span><span class="sxs-lookup"><span data-stu-id="26081-119">View trace logs in the Trace Viewer tool.</span></span>  
  
- <span data-ttu-id="26081-120">Identifier les problèmes liés à WIF dans les journaux de suivi.</span><span class="sxs-lookup"><span data-stu-id="26081-120">Identify WIF related issues in the trace logs.</span></span>  
  
- <span data-ttu-id="26081-121">Prendre des mesures correctives pour les problèmes liés à WIF décelés dans les journaux de suivi.</span><span class="sxs-lookup"><span data-stu-id="26081-121">Apply corrective actions to WIF related issues found in the trace logs.</span></span>  
  
## <a name="summary-of-steps"></a><span data-ttu-id="26081-122">Résumé des étapes</span><span class="sxs-lookup"><span data-stu-id="26081-122">Summary of Steps</span></span>  
  
- <span data-ttu-id="26081-123">Étape 1 : configurer le suivi WIF à l'aide du fichier de configuration Web.config</span><span class="sxs-lookup"><span data-stu-id="26081-123">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
  
- <span data-ttu-id="26081-124">Étape 2 : analyser les fichiers de suivi WIF à l'aide de l'outil Trace Viewer</span><span class="sxs-lookup"><span data-stu-id="26081-124">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
  
- <span data-ttu-id="26081-125">Étape 3 : identifier les solutions pour corriger les problèmes liés à WIF</span><span class="sxs-lookup"><span data-stu-id="26081-125">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
  
## <a name="step-1--configure-wif-tracing-using-webconfig-configuration-file"></a><span data-ttu-id="26081-126">Étape 1 : configurer le suivi WIF à l'aide du fichier de configuration Web.config</span><span class="sxs-lookup"><span data-stu-id="26081-126">Step 1 – Configure WIF Tracing Using Web.config Configuration File</span></span>  
 <span data-ttu-id="26081-127">Dans cette étape, vous allez apporter des modifications aux sections de configuration du fichier *Web.config* pour permettre à WIF de suivre ses événements et les stocker dans un journal de suivi.</span><span class="sxs-lookup"><span data-stu-id="26081-127">In this step, you will add changes to configuration sections in the *Web.config* file that enable WIF to trace its events and store them in a trace log.</span></span>  
  
#### <a name="to-configure-wif-tracing-using-webconfig-configuration-file"></a><span data-ttu-id="26081-128">Pour configurer le suivi WIF à l'aide du fichier de configuration Web.config</span><span class="sxs-lookup"><span data-stu-id="26081-128">To configure WIF tracing using Web.config configuration file</span></span>  
  
1. <span data-ttu-id="26081-129">Ouvrez le fichier de configuration racine **Web.config** ou **App.config** dans l’éditeur Visual Studio en double-cliquant dessus dans l’**Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="26081-129">Open the root **Web.config** or **App.config** configuration file in the Visual Studio editor by double clicking on it in **Solution Explorer**.</span></span> <span data-ttu-id="26081-130">Si votre solution n’a pas de fichier de configuration **Web.config** ou **App.config**, ajoutez-le en cliquant avec le bouton droit sur la solution dans l’**Explorateur de solutions** et en cliquant sur **Ajouter**, puis sur **Nouvel élément...**.</span><span class="sxs-lookup"><span data-stu-id="26081-130">If your solution does not have **Web.config** or **App.config** configuration file, add it by right clicking on the solution in the **Solution Explorer** and clicking **Add**, then clicking **New Item…**.</span></span> <span data-ttu-id="26081-131">Dans la boîte de dialogue **Nouvel élément**, sélectionnez **Fichier de configuration de l’application** pour **App.config** ou **Fichier de configuration web** pour **Web.config** dans la liste, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="26081-131">On the **New Item** dialog, Select **Application Configuration File** for **App.config** or **Web Configuration File** for **Web.config** from the list and click **OK**.</span></span>  
  
2. <span data-ttu-id="26081-132">Ajoutez les entrées de configuration similaires aux suivantes au fichier de configuration dans le nœud **\<configuration>** à la fin du fichier de configuration :</span><span class="sxs-lookup"><span data-stu-id="26081-132">Add the configuration entries similar to the following to the configuration file inside **\<configuration>** node at the end of the configuration file:</span></span>  
  
    ```xml  
    <system.diagnostics>  
        <sources>  
            <source name="System.IdentityModel" switchValue="Verbose">  
                <listeners>  
                    <add name="xml" type="System.Diagnostics.XmlWriterTraceListener" initializeData="WIFTrace.e2e"/>  
                </listeners>  
            </source>  
        </sources>  
        <trace autoflush="true"/>  
    </system.diagnostics>  
    ```  
  
3. <span data-ttu-id="26081-133">La configuration ci-dessus indique à WIF de générer des événements de suivi détaillés et de les consigner dans le fichier *WIFTrace.e2e*.</span><span class="sxs-lookup"><span data-stu-id="26081-133">The above configuration instructs WIF to generate verbose trace events and log them into *WIFTrace.e2e* file.</span></span> <span data-ttu-id="26081-134">Pour obtenir la liste complète des valeurs pour le **switchValue** commutateur, consultez le tableau niveau de Trace dans la rubrique suivante : [Configuration du traçage](../wcf/diagnostics/tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="26081-134">For a complete list of values for the **switchValue** switch, refer to the Trace Level table found in the following topic: [Configuring Tracing](../wcf/diagnostics/tracing/configuring-tracing.md).</span></span>  
  
## <a name="step-2--analyze-wif-trace-files-using-trace-viewer-tool"></a><span data-ttu-id="26081-135">Étape 2 : analyser les fichiers de suivi WIF à l'aide de l'outil Trace Viewer</span><span class="sxs-lookup"><span data-stu-id="26081-135">Step 2 – Analyze WIF Trace Files Using Trace Viewer Tool</span></span>  
 <span data-ttu-id="26081-136">Dans cette étape, vous allez utiliser l'outil Trace Viewer (SvcTraceViewer.exe) pour analyser les journaux de suivi WIF.</span><span class="sxs-lookup"><span data-stu-id="26081-136">In this step, you will use the Trace Viewer Tool (SvcTraceViewer.exe) to analyze WIF trace logs.</span></span>  
  
#### <a name="to-analyze-wif-trace-logs-using-trace-viewer-tool-svctraceviewerexe"></a><span data-ttu-id="26081-137">Pour analyser les journaux de suivi WIF à l'aide de l'outil Trace Viewer (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="26081-137">To analyze WIF trace logs using Trace Viewer tool (SvcTraceViewer.exe)</span></span>  
  
1. <span data-ttu-id="26081-138">L'outil Trace Viewer (SvcTraceViewer.exe) est fourni avec le Kit de développement logiciel (SDK) Windows.</span><span class="sxs-lookup"><span data-stu-id="26081-138">Trace Viewer tool (SvcTraceViewer.exe) ships as part of the Windows SDK.</span></span> <span data-ttu-id="26081-139">Si vous n’avez pas déjà installé le Kit de développement Windows, vous pouvez le télécharger ici : [Windows SDK](https://www.microsoft.com/download/en/details.aspx?id=8279).</span><span class="sxs-lookup"><span data-stu-id="26081-139">If you haven’t already installed the Windows SDK, you can download it here: [Windows SDK](https://www.microsoft.com/download/en/details.aspx?id=8279).</span></span>  
  
2. <span data-ttu-id="26081-140">Exécutez l'outil Trace Viewer (SvcTraceViewer.exe).</span><span class="sxs-lookup"><span data-stu-id="26081-140">Run the Trace Viewer tool (SvcTraceViewer.exe).</span></span> <span data-ttu-id="26081-141">Celui-ci se trouve généralement dans le dossier **Bin** du chemin d’installation.</span><span class="sxs-lookup"><span data-stu-id="26081-141">It is typically available in the **Bin** folder of the installation path.</span></span>  
  
3. <span data-ttu-id="26081-142">Ouvrez le fichier journal de suivi WIF, par exemple WIFTrace.e2e, en sélectionnant l’option **Fichier**, **Ouvrir...**</span><span class="sxs-lookup"><span data-stu-id="26081-142">Open the WIF trace log file, for example, WIFTrace.e2e by selecting **File**, **Open…**</span></span> <span data-ttu-id="26081-143">du menu ou en utilisant le raccourci **Ctrl+O**.</span><span class="sxs-lookup"><span data-stu-id="26081-143">option in the menu or using the **Ctrl+O** shortcut.</span></span> <span data-ttu-id="26081-144">Le fichier journal de suivi s'ouvre dans l'outil Trace Viewer.</span><span class="sxs-lookup"><span data-stu-id="26081-144">The trace log file opens in the Trace Viewer tool.</span></span>  
  
4. <span data-ttu-id="26081-145">Examinez les entrées sous l’onglet **Activité**. Chaque entrée doit contenir un numéro d'activité, le nombre de suivis qui ont été consignés, la durée de l'activité et ses horodateurs de début et de fin.</span><span class="sxs-lookup"><span data-stu-id="26081-145">Review entries in the **Activity** tab. Each entry should contain an activity number, the number of traces that were logged, duration of the activity and its start and end timestamps.</span></span>  
  
5. <span data-ttu-id="26081-146">Cliquez sur l’onglet **Activité**. Des entrées de suivi détaillées doivent s'afficher dans la zone principale de l'outil.</span><span class="sxs-lookup"><span data-stu-id="26081-146">Click on the **Activity** tab. You should see detailed trace entries in the main area of the tool.</span></span> <span data-ttu-id="26081-147">Utilisez le **niveau** liste déroulante dans le menu pour filtrer un niveau spécifique de suivi, par exemple : **Tous les**, **avertissement**, **erreurs**, **informations**, etc.</span><span class="sxs-lookup"><span data-stu-id="26081-147">Use the **Level** dropdown list on the menu to filter specific level of traces, for example: **All**, **Warning**, **Errors**, **Information**, etc.</span></span>  
  
6. <span data-ttu-id="26081-148">Cliquez sur des entrées de suivi spécifiques pour les examiner dans le détail dans la zone inférieure de l’outil.</span><span class="sxs-lookup"><span data-stu-id="26081-148">Click on specific trace entries to review the details in the lower area of the tool.</span></span> <span data-ttu-id="26081-149">Les détails peuvent être visualisés dans la vue **Mis en forme** ou **XML** en choisissant les onglets correspondants.</span><span class="sxs-lookup"><span data-stu-id="26081-149">The details can be viewed using **Formatted** and **XML** view by choosing corresponding tabs.</span></span>  
  
## <a name="step-3--identify-solutions-to-fix-wif-related-issues"></a><span data-ttu-id="26081-150">Étape 3 : identifier les solutions pour corriger les problèmes liés à WIF</span><span class="sxs-lookup"><span data-stu-id="26081-150">Step 3 – Identify Solutions to Fix WIF Related Issues</span></span>  
 <span data-ttu-id="26081-151">Dans cette étape, vous pouvez identifier des solutions pour les problèmes liés à WIF identifiés à l'aide du journal de suivi WIF et de l'outil Trace Viewer.</span><span class="sxs-lookup"><span data-stu-id="26081-151">In this step, you can identify solutions for WIF-related issues identified by using the WIF trace log and Trace Viewer tool.</span></span> <span data-ttu-id="26081-152">Elle établit une correspondance générale entre les exceptions liées à WIF et les solutions potentielles ou les mesures à prendre pour résoudre les problèmes.</span><span class="sxs-lookup"><span data-stu-id="26081-152">It outlines general mapping of WIF related exceptions to potential solutions or required actions to troubleshoot the issue.</span></span>  
  
#### <a name="to-identify-solutions-to-fix-wif-related-issues"></a><span data-ttu-id="26081-153">Pour identifier les solutions en vue de corriger les problèmes liés WIF</span><span class="sxs-lookup"><span data-stu-id="26081-153">To identify solutions to fix WIF related issues</span></span>  
  
1. <span data-ttu-id="26081-154">Consultez ci-dessous le tableau des exceptions WIF et des mesures à prendre pour corriger les problèmes.</span><span class="sxs-lookup"><span data-stu-id="26081-154">Review the following table of WIF exceptions and the required actions to correct the issues.</span></span>  
  
|<span data-ttu-id="26081-155">**ID d’erreur**</span><span class="sxs-lookup"><span data-stu-id="26081-155">**Error ID**</span></span>|<span data-ttu-id="26081-156">**Message d'erreur**</span><span class="sxs-lookup"><span data-stu-id="26081-156">**Error Message**</span></span>|<span data-ttu-id="26081-157">**Mesure à prendre pour corriger l’erreur**</span><span class="sxs-lookup"><span data-stu-id="26081-157">**Action needed to fix the error**</span></span>|  
|-|-|-|  
|<span data-ttu-id="26081-158">ID4175</span><span class="sxs-lookup"><span data-stu-id="26081-158">ID4175</span></span>|<span data-ttu-id="26081-159">L'émetteur du jeton de sécurité n'a pas été reconnu par IssuerNameRegistry.</span><span class="sxs-lookup"><span data-stu-id="26081-159">The issuer of the security token was not recognized by the IssuerNameRegistry.</span></span>  <span data-ttu-id="26081-160">Pour accepter les jetons de sécurité en provenance de cet émetteur, configurez IssuerNameRegistry pour qu'il retourne un nom valide pour cet émetteur.</span><span class="sxs-lookup"><span data-stu-id="26081-160">To accept security tokens from this issuer, configure the IssuerNameRegistry to return a valid name for this issuer.</span></span>|<span data-ttu-id="26081-161">Cette erreur peut être provoquée par la copie d’une empreinte numérique à partir du composant logiciel enfichable MMC et par son collage dans le fichier *Web.config*.</span><span class="sxs-lookup"><span data-stu-id="26081-161">This error can be caused by copying a thumbprint from the MMC snap-in and pasting it into the *Web.config* file.</span></span> <span data-ttu-id="26081-162">Plus précisément, vous pouvez obtenir un caractère non imprimable supplémentaire dans la chaîne de texte en effectuant une copie à partir de la fenêtre de propriétés du certificat.</span><span class="sxs-lookup"><span data-stu-id="26081-162">Specifically, you can get an extra non-printable character in the text string when copying from the certificate properties window.</span></span> <span data-ttu-id="26081-163">Ce caractère supplémentaire entraîne l’échec de la correspondance d’empreinte numérique. Vous trouverez la procédure de copie correctement l’empreinte numérique dans [authentification unique basée sur les revendications-sur pour le Web et Microsoft Azure](https://docs.microsoft.com/previous-versions/msp-n-p/ff359102%28v=pandp.10%29).</span><span class="sxs-lookup"><span data-stu-id="26081-163">This extra character causes the thumbprint match to fail.The procedure for correctly copying the thumbprint can be found at [Claims-Based Single Sign-On for the Web and Microsoft Azure](https://docs.microsoft.com/previous-versions/msp-n-p/ff359102%28v=pandp.10%29).</span></span>|  
  
## <a name="related-items"></a><span data-ttu-id="26081-164">Éléments associés</span><span class="sxs-lookup"><span data-stu-id="26081-164">Related Items</span></span>  
  
- [<span data-ttu-id="26081-165">Utilisation de Service Trace Viewer pour afficher les suivis corrélés et résoudre les problèmes</span><span class="sxs-lookup"><span data-stu-id="26081-165">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
