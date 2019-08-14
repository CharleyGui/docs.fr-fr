---
title: 'Procédure : Activer le suivi WIF'
ms.date: 03/30/2017
ms.assetid: 271b6889-3454-46ff-96ab-9feb15e742ee
author: BrucePerlerMS
ms.openlocfilehash: 40349c5aac7634a515b40a9cc1ab5e75492600c4
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971516"
---
# <a name="how-to-enable-wif-tracing"></a><span data-ttu-id="25b5d-102">Procédure : Activer le suivi WIF</span><span class="sxs-lookup"><span data-stu-id="25b5d-102">How To: Enable WIF Tracing</span></span>

## <a name="applies-to"></a><span data-ttu-id="25b5d-103">S'applique à</span><span class="sxs-lookup"><span data-stu-id="25b5d-103">Applies To</span></span>

- <span data-ttu-id="25b5d-104">Microsoft® Windows® Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="25b5d-104">Microsoft® Windows® Identity Foundation (WIF)</span></span>

- <span data-ttu-id="25b5d-105">Web Forms ASP.NET®</span><span class="sxs-lookup"><span data-stu-id="25b5d-105">ASP.NET® Web Forms</span></span>

## <a name="summary"></a><span data-ttu-id="25b5d-106">Récapitulatif</span><span class="sxs-lookup"><span data-stu-id="25b5d-106">Summary</span></span>

<span data-ttu-id="25b5d-107">Cette procédure fournit des procédures pas à pas détaillées pour l’activation du suivi WIF dans une application ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="25b5d-107">This How-To provides detailed step-by-step procedures for enabling WIF tracing in an ASP.NET application.</span></span> <span data-ttu-id="25b5d-108">Elle fournit également des instructions pour tester l’application afin de vérifier que l’écouteur de suivi et le journal fonctionnent correctement.</span><span class="sxs-lookup"><span data-stu-id="25b5d-108">It also provides instructions testing the application to verify that the trace listener and log are working correctly.</span></span> <span data-ttu-id="25b5d-109">Cette procédure ne fournit pas d'instructions détaillées pour créer un service d'émission de jeton de sécurité (STS, Security Token Service), et utilise à la place le développement STS fourni avec l'outil Identité et accès.</span><span class="sxs-lookup"><span data-stu-id="25b5d-109">This How-To does not have detailed instructions for creating a Security Token Service (STS), and instead uses the Development STS that comes with the Identity and Access tool.</span></span> <span data-ttu-id="25b5d-110">Le développement STS n'exécute de véritable authentification et est destiné à des fins de test uniquement.</span><span class="sxs-lookup"><span data-stu-id="25b5d-110">The Development STS does not perform real authentication and is intended for testing purposes only.</span></span> <span data-ttu-id="25b5d-111">Vous devez installer l'outil Identité et accès pour exécuter cette procédure.</span><span class="sxs-lookup"><span data-stu-id="25b5d-111">You will need to install the Identity and Access tool to complete this How-To.</span></span> <span data-ttu-id="25b5d-112">Il peut être téléchargé à partir de l’emplacement suivant: [Outil identité et accès](https://go.microsoft.com/fwlink/?LinkID=245849)</span><span class="sxs-lookup"><span data-stu-id="25b5d-112">It can be downloaded from the following location: [Identity and Access Tool](https://go.microsoft.com/fwlink/?LinkID=245849)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="25b5d-113">L’activation du suivi WIF pour les applications passives, autrement dit les applications qui utilisent le protocole WS-Federation, peut potentiellement exposer l’application à des attaques par déni de service ou une divulgation d’informations à une personne malveillante.</span><span class="sxs-lookup"><span data-stu-id="25b5d-113">Enabling WIF tracing for passive applications, that is, applications that use the WS-Federation protocol, can potentially expose the application to denial of service (DoS) attacks or to information disclosure to a malicious party.</span></span> <span data-ttu-id="25b5d-114">Cela inclut à la fois les parties de confiance et les services STS passifs.</span><span class="sxs-lookup"><span data-stu-id="25b5d-114">This includes both passive RPs and passive STSes.</span></span> <span data-ttu-id="25b5d-115">Pour cette raison, nous vous recommandons de ne pas activer le suivi WIF pour les parties de confiance ou les services STS passifs dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="25b5d-115">For this reason, we recommend that you not enable WIF tracing for passive RPs or STSes in a production environment.</span></span>

## <a name="contents"></a><span data-ttu-id="25b5d-116">Sommaire</span><span class="sxs-lookup"><span data-stu-id="25b5d-116">Contents</span></span>

- <span data-ttu-id="25b5d-117">Objectifs</span><span class="sxs-lookup"><span data-stu-id="25b5d-117">Objectives</span></span>

- <span data-ttu-id="25b5d-118">Présentation</span><span class="sxs-lookup"><span data-stu-id="25b5d-118">Overview</span></span>

- <span data-ttu-id="25b5d-119">Résumé des étapes</span><span class="sxs-lookup"><span data-stu-id="25b5d-119">Summary of Steps</span></span>

- <span data-ttu-id="25b5d-120">Étape 1 : créer une simple application Web Forms ASP.NET et activer le suivi</span><span class="sxs-lookup"><span data-stu-id="25b5d-120">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>

- <span data-ttu-id="25b5d-121">Étape 2 : tester votre solution</span><span class="sxs-lookup"><span data-stu-id="25b5d-121">Step 2 – Test Your Solution</span></span>

## <a name="objectives"></a><span data-ttu-id="25b5d-122">Objectifs</span><span class="sxs-lookup"><span data-stu-id="25b5d-122">Objectives</span></span>

- <span data-ttu-id="25b5d-123">Créer une simple application ASP.NET qui utilise WIF et le service STS de développement à partir de l’outil Identity and Access Tool</span><span class="sxs-lookup"><span data-stu-id="25b5d-123">Create a simple ASP.NET application that uses WIF and the Development STS from the Identity and Access Tool</span></span>

- <span data-ttu-id="25b5d-124">Activer le suivi et vérifier son fonctionnement</span><span class="sxs-lookup"><span data-stu-id="25b5d-124">Enable tracing and verify that it is working</span></span>

## <a name="overview"></a><span data-ttu-id="25b5d-125">Présentation</span><span class="sxs-lookup"><span data-stu-id="25b5d-125">Overview</span></span>

<span data-ttu-id="25b5d-126">Le suivi vous permet de déboguer et résoudre de nombreux types de problèmes liés à WIF, notamment les jetons, les cookies, les revendications, les messages de protocole et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="25b5d-126">Tracing enables you to debug and troubleshoot many types of issues with WIF, including tokens, cookies, claims, protocol messages, and more.</span></span> <span data-ttu-id="25b5d-127">Le suivi WIF est semblable au suivi WCF ; par exemple, vous pouvez choisir le niveau de détail des suivis pour tout afficher, des messages critiques à l’ensemble des messages.</span><span class="sxs-lookup"><span data-stu-id="25b5d-127">WIF tracing is similar to WCF tracing; for example, you can choose the verbosity of traces to display everything from critical messages to all messages.</span></span> <span data-ttu-id="25b5d-128">Les suivis WIF peuvent être générés dans des fichiers **.xml** ou **.svclog** qui sont visibles à l’aide de l’outil Service Trace Viewer.</span><span class="sxs-lookup"><span data-stu-id="25b5d-128">WIF traces can be generated in **.xml** files or in **.svclog** files that are viewable by using the Service Trace Viewer Tool.</span></span> <span data-ttu-id="25b5d-129">Cet outil se trouve dans le répertoire **bin** du chemin d’installation de SDK Windows sur votre ordinateur, par exemple: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.</span><span class="sxs-lookup"><span data-stu-id="25b5d-129">This tool is located in the **bin** directory of the Windows SDK install path on your computer, for example: **C:\Program Files\Microsoft SDKs\Windows\v7.1\Bin\SvcTraceViewer.exe**.</span></span>

## <a name="summary-of-steps"></a><span data-ttu-id="25b5d-130">Résumé des étapes</span><span class="sxs-lookup"><span data-stu-id="25b5d-130">Summary of Steps</span></span>

- <span data-ttu-id="25b5d-131">Étape 1 : créer une simple application Web Forms ASP.NET et activer le suivi</span><span class="sxs-lookup"><span data-stu-id="25b5d-131">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>

- <span data-ttu-id="25b5d-132">Étape 2 : tester votre solution</span><span class="sxs-lookup"><span data-stu-id="25b5d-132">Step 2 – Test Your Solution</span></span>

## <a name="step-1--create-a-simple-aspnet-web-forms-application-and-enable-tracing"></a><span data-ttu-id="25b5d-133">Étape 1 : créer une simple application Web Forms ASP.NET et activer le suivi</span><span class="sxs-lookup"><span data-stu-id="25b5d-133">Step 1 – Create a Simple ASP.NET Web Forms Application and Enable Tracing</span></span>

<span data-ttu-id="25b5d-134">Dans cette étape, vous allez créer une application Web Forms ASP.NET et modifier le fichier *Web.config* pour activer le suivi.</span><span class="sxs-lookup"><span data-stu-id="25b5d-134">In this step, you will create a new ASP.NET Web Forms application and modify the *Web.config* file to enable tracing.</span></span>

### <a name="to-create-a-simple-aspnet-application"></a><span data-ttu-id="25b5d-135">Pour créer une application ASP.NET simple</span><span class="sxs-lookup"><span data-stu-id="25b5d-135">To create a simple ASP.NET application</span></span>

1. <span data-ttu-id="25b5d-136">Démarrez Visual Studio et cliquez sur **Fichier**, **Nouveau**, puis **Projet**.</span><span class="sxs-lookup"><span data-stu-id="25b5d-136">Start Visual Studio and click **File**, **New**, and then **Project**.</span></span>

2. <span data-ttu-id="25b5d-137">Dans la fenêtre **Nouveau projet**, cliquez sur **Application Web Forms ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="25b5d-137">In the **New Project** window, click **ASP.NET Web Forms Application**.</span></span>

3. <span data-ttu-id="25b5d-138">Dans **Nom**, entrez `TestApp` et appuyez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="25b5d-138">In **Name**, enter `TestApp` and press **OK**.</span></span>

4. <span data-ttu-id="25b5d-139">Cliquez avec le bouton droit sur le projet **TestApp** sous l’**Explorateur de solutions**, puis sélectionnez **Identity and Access** (Identity and Access Tool).</span><span class="sxs-lookup"><span data-stu-id="25b5d-139">Right-click the **TestApp** project under **Solution Explorer**, then select **Identity and Access**.</span></span>

5. <span data-ttu-id="25b5d-140">La fenêtre **Identity and Access** (Identity and Access Tool) s’affiche.</span><span class="sxs-lookup"><span data-stu-id="25b5d-140">The **Identity and Access** window appears.</span></span> <span data-ttu-id="25b5d-141">Sous **Fournisseurs**, sélectionnez **Test your application with the Local Development STS** (Tester votre application avec le service STS de développement local), puis cliquez sur **Appliquer**.</span><span class="sxs-lookup"><span data-stu-id="25b5d-141">Under **Providers**, select **Test your application with the Local Development STS**, then click **Apply**.</span></span>

6. <span data-ttu-id="25b5d-142">Créez un nouveau dossier dans les **journaux** nommés à la racine du lecteur **C:** , comme indiqué ci-dessous: **C:\Logs**</span><span class="sxs-lookup"><span data-stu-id="25b5d-142">Create a new folder in named **logs** in the root of the **C:** drive, like shown: **C:\logs**</span></span>

7. <span data-ttu-id="25b5d-143">Ajoutez l’élément **\<system.diagnostics>** suivant au fichier de configuration *Web.config* immédiatement après l’élément de fermeture **\</configSections>** , comme illustré ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="25b5d-143">Add the following **\<system.diagnostics>** element to the *Web.config* configuration file immediately following the closing **\</configSections>** element, like shown:</span></span>

    ```xml
    <configuration>
        <configSections>
            ...
        </configSections>
        <system.diagnostics>
            <sources>
                <source name="System.IdentityModel" switchValue="Verbose">
                    <listeners>
                        <add name="xml" type="System.Diagnostics.XmlWriterTraceListener" initializeData="C:\logs\WIF.xml" />
                    </listeners>
                </source>
            </sources>
            <trace autoflush="true" />
        </system.diagnostics>
    ```

    > [!NOTE]
    > <span data-ttu-id="25b5d-144">L’emplacement du répertoire spécifié dans l’attribut **initializeData** doit exister avant de commencer la journalisation.</span><span class="sxs-lookup"><span data-stu-id="25b5d-144">The directory location specified in the **initializeData** attribute must exist before logging can begin.</span></span> <span data-ttu-id="25b5d-145">Si l’emplacement n’existe pas, aucun journal n’est créé.</span><span class="sxs-lookup"><span data-stu-id="25b5d-145">If the location does not exist, no logs will be created.</span></span>

     <span data-ttu-id="25b5d-146">Les paramètres de configuration ci-dessus activent le suivi **détaillé** pour WIF et enregistrent le journal obtenu dans le fichier **C:logsWIF.xml**.</span><span class="sxs-lookup"><span data-stu-id="25b5d-146">The configuration settings above will enable **Verbose** tracing for WIF and save the resulting log to the **C:logsWIF.xml** file.</span></span>

## <a name="step-2--test-your-solution"></a><span data-ttu-id="25b5d-147">Étape 2 : tester votre solution</span><span class="sxs-lookup"><span data-stu-id="25b5d-147">Step 2 – Test Your Solution</span></span>

<span data-ttu-id="25b5d-148">Dans cette étape, vous allez tester votre application ASP.NET WIF pour vérifier que les journaux sont enregistrés.</span><span class="sxs-lookup"><span data-stu-id="25b5d-148">In this step, you will test your WIF-enabled ASP.NET application to verify that logs are being recorded.</span></span>

### <a name="to-test-your-wif-enabled-aspnet-application-for-successful-tracing"></a><span data-ttu-id="25b5d-149">Pour tester votre application ASP.NET WIF pour un suivi réussi</span><span class="sxs-lookup"><span data-stu-id="25b5d-149">To test your WIF-enabled ASP.NET application for successful tracing</span></span>

1. <span data-ttu-id="25b5d-150">Exécutez la solution en appuyant sur la touche **F5**.</span><span class="sxs-lookup"><span data-stu-id="25b5d-150">Run the solution by pressing the **F5** key.</span></span> <span data-ttu-id="25b5d-151">La page d’accueil ASP.NET par défaut doit s’afficher et vous devez être automatiquement authentifié avec le nom d’utilisateur *Terry*, qui est l’utilisateur par défaut retourné par le service STS de développement.</span><span class="sxs-lookup"><span data-stu-id="25b5d-151">You should be presented with the default ASP.NET Home Page and automatically authenticated with the username *Terry*, which is the default user that is returned by the Development STS.</span></span>

2. <span data-ttu-id="25b5d-152">Fermez la fenêtre du navigateur et accédez au dossier **C:\logs**.</span><span class="sxs-lookup"><span data-stu-id="25b5d-152">Close the browser window and then navigate to the **C:\logs** folder.</span></span> <span data-ttu-id="25b5d-153">Ouvrez le fichier **C:\logs\WIF.xml** à l’aide d’un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="25b5d-153">Open the **C:\logs\WIF.xml** file using a text editor.</span></span>

3. <span data-ttu-id="25b5d-154">Examinez le fichier **WIF.xml** et vérifiez qu’il contient des entrées commençant par **\<E2ETraceEvent>** .</span><span class="sxs-lookup"><span data-stu-id="25b5d-154">Inspect the **WIF.xml** file and verify that it contains entries starting with **\<E2ETraceEvent>**.</span></span> <span data-ttu-id="25b5d-155">Ces suivis contiennent des éléments **\<TraceRecord>** avec des descriptions de l’activité suivie, par exemple **Validation du SecurityToken**.</span><span class="sxs-lookup"><span data-stu-id="25b5d-155">These traces will contain **\<TraceRecord>** elements with descriptions for the traced activity, such as **Validating SecurityToken**.</span></span>
