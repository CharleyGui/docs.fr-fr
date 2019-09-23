---
title: Déployer un modèle dans une API web ASP.NET Core
description: Alimentez un modèle Machine Learning d’analyse des sentiments ML.NET sur Internet avec l’API web ASP.NET Core.
ms.date: 08/20/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: 8d21ae5ae3aa4701ddd7d042d5069351c22864bb
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182552"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a><span data-ttu-id="8a34a-103">Déployer un modèle dans une API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8a34a-103">Deploy a model in an ASP.NET Core Web API</span></span>

<span data-ttu-id="8a34a-104">Découvrez comment alimenter un modèle Machine Learning ML.NET préentraîné sur le web avec une API web ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="8a34a-104">Learn how to serve a pre-trained ML.NET machine learning model on the web using an ASP.NET Core Web API.</span></span> <span data-ttu-id="8a34a-105">L’alimentation d’un modèle sur une API web permet d’effectuer des prédictions par le biais de méthodes HTTP standard.</span><span class="sxs-lookup"><span data-stu-id="8a34a-105">Serving a model over a web API enables predictions via standard HTTP methods.</span></span>

> [!NOTE]
> <span data-ttu-id="8a34a-106">L’extension de service `PredictionEnginePool` est disponible en préversion.</span><span class="sxs-lookup"><span data-stu-id="8a34a-106">`PredictionEnginePool` service extension is currently in preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8a34a-107">Prérequis</span><span class="sxs-lookup"><span data-stu-id="8a34a-107">Prerequisites</span></span>

- <span data-ttu-id="8a34a-108">[Visual Studio 2017 15.6 ou version ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017), avec la charge de travail « Développement multiplateforme .Net Core » installée.</span><span class="sxs-lookup"><span data-stu-id="8a34a-108">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- <span data-ttu-id="8a34a-109">PowerShell ;</span><span class="sxs-lookup"><span data-stu-id="8a34a-109">Powershell.</span></span>
- <span data-ttu-id="8a34a-110">un modèle préentraîné :</span><span class="sxs-lookup"><span data-stu-id="8a34a-110">Pre-trained model.</span></span> <span data-ttu-id="8a34a-111">Utilisez le [tutoriel Analyse des sentiments dans ML.NET](../tutorials/sentiment-analysis.md) pour générer votre propre modèle ou téléchargez ce [modèle Machine Learning d’analyse des sentiments préentraîné](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip).</span><span class="sxs-lookup"><span data-stu-id="8a34a-111">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-aspnet-core-web-api-project"></a><span data-ttu-id="8a34a-112">Créer un projet d’API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8a34a-112">Create ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="8a34a-113">Ouvrez Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="8a34a-113">Open Visual Studio 2017.</span></span> <span data-ttu-id="8a34a-114">Sélectionnez **Fichier > Nouveau > Projet** dans la barre de menus.</span><span class="sxs-lookup"><span data-stu-id="8a34a-114">Select **File > New > Project** from the menu bar.</span></span> <span data-ttu-id="8a34a-115">Dans la boîte de dialogue Nouveau projet, sélectionnez le nœud **Visual C#** , suivi du nœud **Web**.</span><span class="sxs-lookup"><span data-stu-id="8a34a-115">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="8a34a-116">Ensuite, sélectionnez le modèle de projet **Application web ASP.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="8a34a-116">Then select the **ASP.NET Core Web Application** project template.</span></span> <span data-ttu-id="8a34a-117">Dans la zone de texte **Nom**, tapez « SentimentAnalysisWebAPI », puis sélectionnez le bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="8a34a-117">In the **Name** text box, type "SentimentAnalysisWebAPI" and then select the **OK** button.</span></span>

1. <span data-ttu-id="8a34a-118">Dans la fenêtre qui affiche les différents types de projets ASP.NET Core, sélectionnez **API**, puis le bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="8a34a-118">In the window that displays the different types of ASP.NET Core Projects, select **API** and the select the **OK** button.</span></span>

1. <span data-ttu-id="8a34a-119">Créez un répertoire nommé *MLModels* dans votre projet pour enregistrer les fichiers de votre modèle Machine Learning prédéfini :</span><span class="sxs-lookup"><span data-stu-id="8a34a-119">Create a directory named *MLModels* in your project to save your pre-built machine learning model files:</span></span>

    <span data-ttu-id="8a34a-120">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur votre projet et sélectionnez Ajouter > Nouveau dossier.</span><span class="sxs-lookup"><span data-stu-id="8a34a-120">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="8a34a-121">Tapez « MLModels » et appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="8a34a-121">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="8a34a-122">Installez le **package NuGet Microsoft.ML** :</span><span class="sxs-lookup"><span data-stu-id="8a34a-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="8a34a-123">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Gérer les packages NuGet**.</span><span class="sxs-lookup"><span data-stu-id="8a34a-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="8a34a-124">Choisissez « nuget.org » comme Source du package, sélectionnez l’onglet Parcourir, recherchez **Microsoft.ML**, sélectionnez ce package dans la liste, puis sélectionnez le bouton Installer.</span><span class="sxs-lookup"><span data-stu-id="8a34a-124">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="8a34a-125">Sélectionnez le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis le bouton **J’accepte** dans la boîte de dialogue Acceptation de la licence si vous acceptez les termes du contrat de licence pour les packages de la liste.</span><span class="sxs-lookup"><span data-stu-id="8a34a-125">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="8a34a-126">Installez le **package NuGet Microsoft.Extensions.ML** :</span><span class="sxs-lookup"><span data-stu-id="8a34a-126">Install the **Microsoft.Extensions.ML Nuget Package**:</span></span>

    <span data-ttu-id="8a34a-127">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Gérer les packages NuGet**.</span><span class="sxs-lookup"><span data-stu-id="8a34a-127">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="8a34a-128">Choisissez « nuget.org » comme Source du package, sélectionnez l’onglet Parcourir, recherchez **Microsoft.Extensions.ML**, sélectionnez ce package dans la liste, puis sélectionnez le bouton Installer.</span><span class="sxs-lookup"><span data-stu-id="8a34a-128">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="8a34a-129">Sélectionnez le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis le bouton **J’accepte** dans la boîte de dialogue Acceptation de la licence si vous acceptez les termes du contrat de licence pour les packages de la liste.</span><span class="sxs-lookup"><span data-stu-id="8a34a-129">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="add-model-to-aspnet-core-web-api-project"></a><span data-ttu-id="8a34a-130">Ajouter un modèle au projet d’API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8a34a-130">Add model to ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="8a34a-131">Copiez votre modèle prédéfini dans le répertoire *MLModels*.</span><span class="sxs-lookup"><span data-stu-id="8a34a-131">Copy your pre-built model to the *MLModels* directory</span></span>
1. <span data-ttu-id="8a34a-132">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le fichier zip du modèle et sélectionnez Propriétés.</span><span class="sxs-lookup"><span data-stu-id="8a34a-132">In Solution Explorer, right-click the model zip file and select Properties.</span></span> <span data-ttu-id="8a34a-133">Sous Avancé, remplacez la valeur Copier dans le répertoire de sortie par Copier si plus récent.</span><span class="sxs-lookup"><span data-stu-id="8a34a-133">Under Advanced, change the value of Copy to Output Directory to Copy if newer.</span></span>

## <a name="create-data-models"></a><span data-ttu-id="8a34a-134">Créer des modèles de données</span><span class="sxs-lookup"><span data-stu-id="8a34a-134">Create data models</span></span>

<span data-ttu-id="8a34a-135">Vous devez créer des classes pour vos données d’entrée et prévisions.</span><span class="sxs-lookup"><span data-stu-id="8a34a-135">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="8a34a-136">Ajoutez une nouvelle classe à votre projet :</span><span class="sxs-lookup"><span data-stu-id="8a34a-136">Add a new class to your project:</span></span>

1. <span data-ttu-id="8a34a-137">Créez un répertoire nommé *DataModels* dans votre projet pour enregistrer vos modèles de données :</span><span class="sxs-lookup"><span data-stu-id="8a34a-137">Create a directory named *DataModels* in your project to save your data models:</span></span>

    <span data-ttu-id="8a34a-138">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur votre projet et sélectionnez Ajouter > Nouveau dossier.</span><span class="sxs-lookup"><span data-stu-id="8a34a-138">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="8a34a-139">Tapez « DataModels » et appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="8a34a-139">Type "DataModels" and hit **Enter**.</span></span>

2. <span data-ttu-id="8a34a-140">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le répertoire *DataModels*, puis sélectionnez Ajouter > Nouvel élément.</span><span class="sxs-lookup"><span data-stu-id="8a34a-140">In Solution Explorer, right-click the *DataModels* directory, and then select Add > New Item.</span></span>
3. <span data-ttu-id="8a34a-141">Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe**, puis remplacez la valeur du champ **Nom** par *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="8a34a-141">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="8a34a-142">Ensuite, sélectionnez le bouton **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="8a34a-142">Then, select the **Add** button.</span></span> <span data-ttu-id="8a34a-143">Le fichier *SentimentData.cs* s’ouvre dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="8a34a-143">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="8a34a-144">Ajoutez l’instruction using suivante en haut du fichier *SentimentData.cs* :</span><span class="sxs-lookup"><span data-stu-id="8a34a-144">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    <span data-ttu-id="8a34a-145">Supprimez la définition de classe existante et ajoutez le code suivant au fichier **SentimentData.cs** :</span><span class="sxs-lookup"><span data-stu-id="8a34a-145">Remove the existing class definition and add the following code to the **SentimentData.cs** file:</span></span>
    
    ```csharp
    public class SentimentData
    {
        [LoadColumn(0)]
        public string SentimentText;

        [LoadColumn(1)]
        [ColumnName("Label")]
        public bool Sentiment;
    }
    ```

4. <span data-ttu-id="8a34a-146">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le répertoire *DataModels*, puis sélectionnez **Ajouter > Nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="8a34a-146">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="8a34a-147">Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et remplacez la valeur du champ **Nom** par *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="8a34a-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="8a34a-148">Ensuite, sélectionnez le bouton Ajouter.</span><span class="sxs-lookup"><span data-stu-id="8a34a-148">Then, select the Add button.</span></span> <span data-ttu-id="8a34a-149">Le fichier *SentimentPrediction.cs* s’ouvre dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="8a34a-149">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="8a34a-150">Ajoutez l’instruction using suivante en haut du fichier *SentimentPrediction.cs* :</span><span class="sxs-lookup"><span data-stu-id="8a34a-150">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```
    
    <span data-ttu-id="8a34a-151">Supprimez la définition de classe existante et ajoutez le code suivant au fichier *SentimentPrediction.cs* :</span><span class="sxs-lookup"><span data-stu-id="8a34a-151">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>
    
    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="8a34a-152">`SentimentPrediction` hérite de `SentimentData`.</span><span class="sxs-lookup"><span data-stu-id="8a34a-152">`SentimentPrediction` inherits from `SentimentData`.</span></span> <span data-ttu-id="8a34a-153">Vous pouvez ainsi mieux voir les données d’origine dans la propriété `SentimentText` ainsi que la sortie générée par le modèle.</span><span class="sxs-lookup"><span data-stu-id="8a34a-153">This makes it easier to see the original data in the `SentimentText` property along with the output generated by the model.</span></span> 

## <a name="register-predictionenginepool-for-use-in-the-application"></a><span data-ttu-id="8a34a-154">Inscrire PredictionEnginePool pour l’utiliser dans l’application</span><span class="sxs-lookup"><span data-stu-id="8a34a-154">Register PredictionEnginePool for use in the application</span></span>

<span data-ttu-id="8a34a-155">Pour établir une prédiction unique, utilisez [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="8a34a-155">To make a single prediction, use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="8a34a-156">Pour pouvoir utiliser la classe [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) dans votre application, vous devez la créer quand vous en avez besoin.</span><span class="sxs-lookup"><span data-stu-id="8a34a-156">In order to use [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) in your application you must create it when it's needed.</span></span> <span data-ttu-id="8a34a-157">Dans ce cas, il est recommandé d’utiliser l’injection de dépendances.</span><span class="sxs-lookup"><span data-stu-id="8a34a-157">In that case, a best practice to consider is dependency injection.</span></span>

<span data-ttu-id="8a34a-158">Pour plus d’informations, consultez [Injection de dépendances dans ASP.NET Core](/aspnet/core/fundamentals/dependency-injection).</span><span class="sxs-lookup"><span data-stu-id="8a34a-158">The following link provides more information if you want to learn about [dependency injection in ASP.NET Core](/aspnet/core/fundamentals/dependency-injection).</span></span>

1. <span data-ttu-id="8a34a-159">Ouvrez la classe *Startup.cs* et ajoutez l’instruction using suivante en haut du fichier :</span><span class="sxs-lookup"><span data-stu-id="8a34a-159">Open the *Startup.cs* class and add the following using statement to the top of the file:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. <span data-ttu-id="8a34a-160">Ajoutez le code suivant à la méthode *ConfigureServices* :</span><span class="sxs-lookup"><span data-stu-id="8a34a-160">Add the following code to the *ConfigureServices* method:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_1);
        services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
            .FromFile("MLModels/sentiment_model.zip");
    }
    ```

<span data-ttu-id="8a34a-161">À haut niveau, ce code initialise automatiquement les objets et les services à la demande de l’application, ce qui évite d’avoir à le faire manuellement.</span><span class="sxs-lookup"><span data-stu-id="8a34a-161">At a high level, this code initializes the objects and services automatically when requested by the application instead of having to manually do it.</span></span>

> [!WARNING]
> <span data-ttu-id="8a34a-162">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) n’est pas thread‑safe.</span><span class="sxs-lookup"><span data-stu-id="8a34a-162">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="8a34a-163">Pour améliorer les performances et la cohérence de thread, utilisez le service `PredictionEnginePool`, qui crée un [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) d’objets `PredictionEngine` à utiliser avec l’application.</span><span class="sxs-lookup"><span data-stu-id="8a34a-163">For improved performance and thread safety, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of `PredictionEngine` objects for application use.</span></span> <span data-ttu-id="8a34a-164">Lisez le billet de blog suivant pour en savoir plus sur [la création et l’utilisation de pools d’objets `PredictionEngine` dans ASP.NET Core](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span><span class="sxs-lookup"><span data-stu-id="8a34a-164">Read the following blog post to learn more about [creating and using `PredictionEngine` object pools in ASP.NET Core](https://devblogs.microsoft.com/cesardelatorre/how-to-optimize-and-run-ml-net-models-on-scalable-asp-net-core-webapis-or-web-apps/).</span></span>  

## <a name="create-predict-controller"></a><span data-ttu-id="8a34a-165">Créer un contrôleur de prédictions</span><span class="sxs-lookup"><span data-stu-id="8a34a-165">Create Predict controller</span></span>

<span data-ttu-id="8a34a-166">Pour traiter les requêtes HTTP entrantes, créez un contrôleur.</span><span class="sxs-lookup"><span data-stu-id="8a34a-166">To process your incoming HTTP requests, create a controller.</span></span>

1. <span data-ttu-id="8a34a-167">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le répertoire *Contrôleurs*, puis sélectionnez **Ajouter > Contrôleur**.</span><span class="sxs-lookup"><span data-stu-id="8a34a-167">In Solution Explorer, right-click the *Controllers* directory, and then select **Add > Controller**.</span></span>
1. <span data-ttu-id="8a34a-168">Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Contrôleur d’API vide** et **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="8a34a-168">In the **Add New Item** dialog box, select **API Controller Empty** and select **Add**.</span></span>
1. <span data-ttu-id="8a34a-169">À l’invite, remplacez la valeur du champ **Nom du contrôleur** par *PredictController.cs*.</span><span class="sxs-lookup"><span data-stu-id="8a34a-169">In the prompt change the **Controller Name** field to *PredictController.cs*.</span></span> <span data-ttu-id="8a34a-170">Ensuite, sélectionnez le bouton Ajouter.</span><span class="sxs-lookup"><span data-stu-id="8a34a-170">Then, select the Add button.</span></span> <span data-ttu-id="8a34a-171">Le fichier *PredictController.cs* s’ouvre dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="8a34a-171">The *PredictController.cs* file opens in the code editor.</span></span> <span data-ttu-id="8a34a-172">Ajoutez l’instruction using suivante en haut du fichier *PredictController.cs* :</span><span class="sxs-lookup"><span data-stu-id="8a34a-172">Add the following using statement to the top of *PredictController.cs*:</span></span>

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    <span data-ttu-id="8a34a-173">Supprimez la définition de classe existante et ajoutez le code suivant au fichier *PredictController.cs* :</span><span class="sxs-lookup"><span data-stu-id="8a34a-173">Remove the existing class definition and add the following code to the *PredictController.cs* file:</span></span>
    
    ```csharp
    public class PredictController : ControllerBase
    {
        private readonly PredictionEnginePool<SentimentData, SentimentPrediction> _predictionEnginePool;

        public PredictController(PredictionEnginePool<SentimentData,SentimentPrediction> predictionEnginePool)
        {
            _predictionEnginePool = predictionEnginePool;
        }

        [HttpPost]
        public ActionResult<string> Post([FromBody] SentimentData input)
        {
            if(!ModelState.IsValid)
            {
                return BadRequest();
            }

            SentimentPrediction prediction = _predictionEnginePool.Predict(input);

            string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

            return Ok(sentiment);
        }
    }
    ```

<span data-ttu-id="8a34a-174">Ce code affecte le `PredictionEnginePool` en le passant au constructeur du contrôleur, obtenu par injection de dépendances.</span><span class="sxs-lookup"><span data-stu-id="8a34a-174">This code assigns the `PredictionEnginePool` by passing it to the controller's constructor which you get via dependency injection.</span></span> <span data-ttu-id="8a34a-175">Ensuite, la méthode `Post` du contrôleur `Predict` utilise le `PredictionEnginePool` pour établir des prédictions et retourner les résultats à l’utilisateur en cas de réussite.</span><span class="sxs-lookup"><span data-stu-id="8a34a-175">Then, the `Predict` controller's `Post` method uses the `PredictionEnginePool` to make predictions and return the results back to the user if successful.</span></span>

## <a name="test-web-api-locally"></a><span data-ttu-id="8a34a-176">Tester l’API web localement</span><span class="sxs-lookup"><span data-stu-id="8a34a-176">Test web API locally</span></span>

<span data-ttu-id="8a34a-177">Maintenant que tout est configuré, il est temps de tester l’application.</span><span class="sxs-lookup"><span data-stu-id="8a34a-177">Once everything is set up, it's time to test the application.</span></span>

1. <span data-ttu-id="8a34a-178">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="8a34a-178">Run the application.</span></span>
1. <span data-ttu-id="8a34a-179">Ouvrez PowerShell et entrez le code suivant, où PORT est le port d’écoute de votre application.</span><span class="sxs-lookup"><span data-stu-id="8a34a-179">Open Powershell and enter the following code where PORT is the port your application is listening on.</span></span>

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{SentimentText="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="8a34a-180">En cas de réussite, la sortie devrait se présenter ainsi :</span><span class="sxs-lookup"><span data-stu-id="8a34a-180">If successful, the output should look similar to the text below:</span></span>
    
    ```powershell
    Negative
    ```

<span data-ttu-id="8a34a-181">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="8a34a-181">Congratulations!</span></span> <span data-ttu-id="8a34a-182">Vous avez réussi à alimenter votre modèle de façon à effectuer des prédictions sur Internet à l’aide d’une API web ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="8a34a-182">You have successfully served your model to make predictions over the internet using an ASP.NET Core Web API.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8a34a-183">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="8a34a-183">Next Steps</span></span>

- [<span data-ttu-id="8a34a-184">Déployer sur Azure</span><span class="sxs-lookup"><span data-stu-id="8a34a-184">Deploy to Azure</span></span>](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs#deploy-the-app-to-azure)
