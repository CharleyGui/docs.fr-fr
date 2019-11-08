---
title: Déployer un modèle dans une API web ASP.NET Core
description: Alimentez un modèle Machine Learning d’analyse des sentiments ML.NET sur Internet avec l’API web ASP.NET Core.
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: b6801b7de5a17257be706f77a7a67aa87df96524
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733306"
---
# <a name="deploy-a-model-in-an-aspnet-core-web-api"></a><span data-ttu-id="7273c-103">Déployer un modèle dans une API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7273c-103">Deploy a model in an ASP.NET Core Web API</span></span>

<span data-ttu-id="7273c-104">Découvrez comment alimenter un modèle Machine Learning ML.NET préentraîné sur le web avec une API web ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="7273c-104">Learn how to serve a pre-trained ML.NET machine learning model on the web using an ASP.NET Core Web API.</span></span> <span data-ttu-id="7273c-105">L’alimentation d’un modèle sur une API web permet d’effectuer des prédictions par le biais de méthodes HTTP standard.</span><span class="sxs-lookup"><span data-stu-id="7273c-105">Serving a model over a web API enables predictions via standard HTTP methods.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7273c-106">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7273c-106">Prerequisites</span></span>

- <span data-ttu-id="7273c-107">[Visual Studio 2017 version 15,6 ou ultérieure](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) avec la charge de travail « développement multiplateforme .net Core » installée.</span><span class="sxs-lookup"><span data-stu-id="7273c-107">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>
- <span data-ttu-id="7273c-108">PowerShell ;</span><span class="sxs-lookup"><span data-stu-id="7273c-108">Powershell.</span></span>
- <span data-ttu-id="7273c-109">un modèle préentraîné :</span><span class="sxs-lookup"><span data-stu-id="7273c-109">Pre-trained model.</span></span> <span data-ttu-id="7273c-110">Utilisez le [tutoriel Analyse des sentiments dans ML.NET](../tutorials/sentiment-analysis.md) pour générer votre propre modèle ou téléchargez ce [modèle Machine Learning d’analyse des sentiments préentraîné](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip).</span><span class="sxs-lookup"><span data-stu-id="7273c-110">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="create-aspnet-core-web-api-project"></a><span data-ttu-id="7273c-111">Créer un projet d’API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7273c-111">Create ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="7273c-112">Ouvrez Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="7273c-112">Open Visual Studio 2017.</span></span> <span data-ttu-id="7273c-113">Sélectionnez **Fichier > Nouveau > Projet** dans la barre de menus.</span><span class="sxs-lookup"><span data-stu-id="7273c-113">Select **File > New > Project** from the menu bar.</span></span> <span data-ttu-id="7273c-114">Dans la boîte de dialogue Nouveau projet, sélectionnez le nœud **Visual C#** , suivi du nœud **Web**.</span><span class="sxs-lookup"><span data-stu-id="7273c-114">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span> <span data-ttu-id="7273c-115">Ensuite, sélectionnez le modèle de projet **Application web ASP.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="7273c-115">Then select the **ASP.NET Core Web Application** project template.</span></span> <span data-ttu-id="7273c-116">Dans la zone de texte **Nom**, tapez « SentimentAnalysisWebAPI », puis sélectionnez le bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="7273c-116">In the **Name** text box, type "SentimentAnalysisWebAPI" and then select the **OK** button.</span></span>

1. <span data-ttu-id="7273c-117">Dans la fenêtre qui affiche les différents types de projets ASP.NET Core, sélectionnez **API**, puis le bouton **OK**.</span><span class="sxs-lookup"><span data-stu-id="7273c-117">In the window that displays the different types of ASP.NET Core Projects, select **API** and the select the **OK** button.</span></span>

1. <span data-ttu-id="7273c-118">Créez un répertoire nommé *MLModels* dans votre projet pour enregistrer les fichiers de votre modèle Machine Learning prédéfini :</span><span class="sxs-lookup"><span data-stu-id="7273c-118">Create a directory named *MLModels* in your project to save your pre-built machine learning model files:</span></span>

    <span data-ttu-id="7273c-119">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur votre projet et sélectionnez Ajouter > Nouveau dossier.</span><span class="sxs-lookup"><span data-stu-id="7273c-119">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="7273c-120">Tapez « MLModels » et appuyez sur Entrée.</span><span class="sxs-lookup"><span data-stu-id="7273c-120">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="7273c-121">Installez le **package NuGet Microsoft.ML** :</span><span class="sxs-lookup"><span data-stu-id="7273c-121">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="7273c-122">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Gérer les packages NuGet**.</span><span class="sxs-lookup"><span data-stu-id="7273c-122">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="7273c-123">Choisissez « nuget.org » comme Source du package, sélectionnez l’onglet Parcourir, recherchez **Microsoft.ML**, sélectionnez ce package dans la liste, puis sélectionnez le bouton Installer.</span><span class="sxs-lookup"><span data-stu-id="7273c-123">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="7273c-124">Sélectionnez le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis le bouton **J’accepte** dans la boîte de dialogue Acceptation de la licence si vous acceptez les termes du contrat de licence pour les packages de la liste.</span><span class="sxs-lookup"><span data-stu-id="7273c-124">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="7273c-125">Installez le **package NuGet Microsoft.Extensions.ML** :</span><span class="sxs-lookup"><span data-stu-id="7273c-125">Install the **Microsoft.Extensions.ML Nuget Package**:</span></span>

    <span data-ttu-id="7273c-126">Dans l'Explorateur de solutions, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Gérer les packages NuGet**.</span><span class="sxs-lookup"><span data-stu-id="7273c-126">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="7273c-127">Choisissez « nuget.org » comme Source du package, sélectionnez l’onglet Parcourir, recherchez **Microsoft.Extensions.ML**, sélectionnez ce package dans la liste, puis sélectionnez le bouton Installer.</span><span class="sxs-lookup"><span data-stu-id="7273c-127">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the Install button.</span></span> <span data-ttu-id="7273c-128">Sélectionnez le bouton **OK** dans la boîte de dialogue **Aperçu des modifications**, puis le bouton **J’accepte** dans la boîte de dialogue Acceptation de la licence si vous acceptez les termes du contrat de licence pour les packages de la liste.</span><span class="sxs-lookup"><span data-stu-id="7273c-128">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="add-model-to-aspnet-core-web-api-project"></a><span data-ttu-id="7273c-129">Ajouter un modèle au projet d’API web ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="7273c-129">Add model to ASP.NET Core Web API project</span></span>

1. <span data-ttu-id="7273c-130">Copiez votre modèle prédéfini dans le répertoire *MLModels*.</span><span class="sxs-lookup"><span data-stu-id="7273c-130">Copy your pre-built model to the *MLModels* directory</span></span>
1. <span data-ttu-id="7273c-131">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le fichier zip du modèle et sélectionnez Propriétés.</span><span class="sxs-lookup"><span data-stu-id="7273c-131">In Solution Explorer, right-click the model zip file and select Properties.</span></span> <span data-ttu-id="7273c-132">Sous Avancé, remplacez la valeur Copier dans le répertoire de sortie par Copier si plus récent.</span><span class="sxs-lookup"><span data-stu-id="7273c-132">Under Advanced, change the value of Copy to Output Directory to Copy if newer.</span></span>

## <a name="create-data-models"></a><span data-ttu-id="7273c-133">Créer des modèles de données</span><span class="sxs-lookup"><span data-stu-id="7273c-133">Create data models</span></span>

<span data-ttu-id="7273c-134">Vous devez créer des classes pour vos données d’entrée et prévisions.</span><span class="sxs-lookup"><span data-stu-id="7273c-134">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="7273c-135">Ajoutez une nouvelle classe à votre projet :</span><span class="sxs-lookup"><span data-stu-id="7273c-135">Add a new class to your project:</span></span>

1. <span data-ttu-id="7273c-136">Créez un répertoire nommé *DataModels* dans votre projet pour enregistrer vos modèles de données :</span><span class="sxs-lookup"><span data-stu-id="7273c-136">Create a directory named *DataModels* in your project to save your data models:</span></span>

    <span data-ttu-id="7273c-137">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur votre projet et sélectionnez Ajouter > Nouveau dossier.</span><span class="sxs-lookup"><span data-stu-id="7273c-137">In Solution Explorer, right-click on your project and select Add > New Folder.</span></span> <span data-ttu-id="7273c-138">Tapez « DataModels » et appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="7273c-138">Type "DataModels" and hit **Enter**.</span></span>

2. <span data-ttu-id="7273c-139">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le répertoire *DataModels*, puis sélectionnez Ajouter > Nouvel élément.</span><span class="sxs-lookup"><span data-stu-id="7273c-139">In Solution Explorer, right-click the *DataModels* directory, and then select Add > New Item.</span></span>
3. <span data-ttu-id="7273c-140">Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe**, puis remplacez la valeur du champ **Nom** par *SentimentData.cs*.</span><span class="sxs-lookup"><span data-stu-id="7273c-140">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="7273c-141">Ensuite, sélectionnez le bouton **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="7273c-141">Then, select the **Add** button.</span></span> <span data-ttu-id="7273c-142">Le fichier *SentimentData.cs* s’ouvre dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="7273c-142">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="7273c-143">Ajoutez l’instruction using suivante en haut du fichier *SentimentData.cs* :</span><span class="sxs-lookup"><span data-stu-id="7273c-143">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="7273c-144">Supprimez la définition de classe existante et ajoutez le code suivant au fichier **SentimentData.cs** :</span><span class="sxs-lookup"><span data-stu-id="7273c-144">Remove the existing class definition and add the following code to the **SentimentData.cs** file:</span></span>

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

4. <span data-ttu-id="7273c-145">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le répertoire *DataModels*, puis sélectionnez **Ajouter > Nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="7273c-145">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="7273c-146">Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Classe** et remplacez la valeur du champ **Nom** par *SentimentPrediction.cs*.</span><span class="sxs-lookup"><span data-stu-id="7273c-146">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="7273c-147">Ensuite, sélectionnez le bouton Ajouter.</span><span class="sxs-lookup"><span data-stu-id="7273c-147">Then, select the Add button.</span></span> <span data-ttu-id="7273c-148">Le fichier *SentimentPrediction.cs* s’ouvre dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="7273c-148">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="7273c-149">Ajoutez l’instruction using suivante en haut du fichier *SentimentPrediction.cs* :</span><span class="sxs-lookup"><span data-stu-id="7273c-149">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    ```csharp
    using Microsoft.ML.Data;
    ```

    <span data-ttu-id="7273c-150">Supprimez la définition de classe existante et ajoutez le code suivant au fichier *SentimentPrediction.cs* :</span><span class="sxs-lookup"><span data-stu-id="7273c-150">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    ```csharp
    public class SentimentPrediction : SentimentData
    {

        [ColumnName("PredictedLabel")]
        public bool Prediction { get; set; }

        public float Probability { get; set; }

        public float Score { get; set; }
    }
    ```

    <span data-ttu-id="7273c-151">`SentimentPrediction` hérite de `SentimentData`.</span><span class="sxs-lookup"><span data-stu-id="7273c-151">`SentimentPrediction` inherits from `SentimentData`.</span></span> <span data-ttu-id="7273c-152">Vous pouvez ainsi mieux voir les données d’origine dans la propriété `SentimentText` ainsi que la sortie générée par le modèle.</span><span class="sxs-lookup"><span data-stu-id="7273c-152">This makes it easier to see the original data in the `SentimentText` property along with the output generated by the model.</span></span>

## <a name="register-predictionenginepool-for-use-in-the-application"></a><span data-ttu-id="7273c-153">Inscrire PredictionEnginePool pour l’utiliser dans l’application</span><span class="sxs-lookup"><span data-stu-id="7273c-153">Register PredictionEnginePool for use in the application</span></span>

<span data-ttu-id="7273c-154">Pour effectuer une prédiction unique, vous devez créer un [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span><span class="sxs-lookup"><span data-stu-id="7273c-154">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="7273c-155">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) n’est pas thread‑safe.</span><span class="sxs-lookup"><span data-stu-id="7273c-155">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="7273c-156">En outre, vous devez créer une instance de celle-ci partout où elle est nécessaire dans votre application.</span><span class="sxs-lookup"><span data-stu-id="7273c-156">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="7273c-157">À mesure que votre application croît, ce processus peut devenir non gérable.</span><span class="sxs-lookup"><span data-stu-id="7273c-157">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="7273c-158">Pour améliorer les performances et la sécurité des threads, utilisez une combinaison d’injection de dépendances et le service `PredictionEnginePool`, qui crée un [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) d’objets [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) pour une utilisation dans votre application.</span><span class="sxs-lookup"><span data-stu-id="7273c-158">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

<span data-ttu-id="7273c-159">Le lien suivant fournit plus d’informations si vous souhaitez en savoir plus sur [l’injection de dépendances dans ASP.net Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span><span class="sxs-lookup"><span data-stu-id="7273c-159">The following link provides more information if you want to learn more about [dependency injection in ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-2.1).</span></span>

1. <span data-ttu-id="7273c-160">Ouvrez la classe *Startup.cs* et ajoutez l’instruction using suivante en haut du fichier :</span><span class="sxs-lookup"><span data-stu-id="7273c-160">Open the *Startup.cs* class and add the following using statement to the top of the file:</span></span>

    ```csharp
    using Microsoft.AspNetCore.Builder;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.Configuration;
    using Microsoft.Extensions.DependencyInjection;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

2. <span data-ttu-id="7273c-161">Ajoutez le code suivant à la méthode *ConfigureServices* :</span><span class="sxs-lookup"><span data-stu-id="7273c-161">Add the following code to the *ConfigureServices* method:</span></span>

    ```csharp
    services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
        .FromFile(modelName: "SentimentAnalysisModel", filePath:"MLModels/sentiment_model.zip", watchForChanges: true);
    ```

<span data-ttu-id="7273c-162">À un niveau élevé, ce code initialise automatiquement les objets et les services en vue d’une utilisation ultérieure lorsqu’ils sont demandés par l’application au lieu d’avoir à le faire manuellement.</span><span class="sxs-lookup"><span data-stu-id="7273c-162">At a high level, this code initializes the objects and services automatically for later use when requested by the application instead of having to manually do it.</span></span>

<span data-ttu-id="7273c-163">Les modèles machine learning ne sont pas statiques.</span><span class="sxs-lookup"><span data-stu-id="7273c-163">Machine learning models are not static.</span></span> <span data-ttu-id="7273c-164">À mesure que de nouvelles données d’apprentissage deviennent disponibles, le modèle est reformé et redéployé.</span><span class="sxs-lookup"><span data-stu-id="7273c-164">As new training data becomes available, the model is retrained and redeployed.</span></span> <span data-ttu-id="7273c-165">Une façon d’utiliser la dernière version du modèle dans votre application consiste à redéployer l’application entière.</span><span class="sxs-lookup"><span data-stu-id="7273c-165">One way to get the latest version of the model into your application is to redeploy the entire application.</span></span> <span data-ttu-id="7273c-166">Toutefois, cela entraîne un temps d’arrêt des applications.</span><span class="sxs-lookup"><span data-stu-id="7273c-166">However, this introduces application downtime.</span></span> <span data-ttu-id="7273c-167">Le service `PredictionEnginePool` fournit un mécanisme permettant de recharger un modèle mis à jour sans mettre votre application hors service.</span><span class="sxs-lookup"><span data-stu-id="7273c-167">The `PredictionEnginePool` service provides a mechanism to reload an updated model without taking your application down.</span></span>

<span data-ttu-id="7273c-168">Définissez le paramètre `watchForChanges` sur `true`, et le `PredictionEnginePool` démarre un [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) qui écoute les notifications de modification du système de fichiers et déclenche des événements lorsqu’une modification est apportée au fichier.</span><span class="sxs-lookup"><span data-stu-id="7273c-168">Set the `watchForChanges` parameter to `true`, and the `PredictionEnginePool` starts a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) that listens to the file system change notifications and raises events when there is a change to the file.</span></span> <span data-ttu-id="7273c-169">Cela invite le `PredictionEnginePool` à recharger automatiquement le modèle.</span><span class="sxs-lookup"><span data-stu-id="7273c-169">This prompts the `PredictionEnginePool` to automatically reload the model.</span></span>

<span data-ttu-id="7273c-170">Le modèle est identifié par le paramètre `modelName` afin que plusieurs modèles par application puissent être rechargés une fois la modification apportée.</span><span class="sxs-lookup"><span data-stu-id="7273c-170">The model is identified by the `modelName` parameter so that more than one model per application can be reloaded upon change.</span></span>

> [!TIP]
> <span data-ttu-id="7273c-171">Vous pouvez également utiliser la méthode `FromUri` lorsque vous travaillez avec des modèles stockés à distance.</span><span class="sxs-lookup"><span data-stu-id="7273c-171">Alternatively, you can use the `FromUri` method when working with models stored remotely.</span></span> <span data-ttu-id="7273c-172">Au lieu d’observer les événements de modification de fichier, `FromUri` interroge l’emplacement distant pour les modifications.</span><span class="sxs-lookup"><span data-stu-id="7273c-172">Rather than watching for file changed events, `FromUri` polls the remote location for changes.</span></span> <span data-ttu-id="7273c-173">La valeur par défaut de l’intervalle d’interrogation est de 5 minutes.</span><span class="sxs-lookup"><span data-stu-id="7273c-173">The polling interval defaults to 5 minutes.</span></span> <span data-ttu-id="7273c-174">Vous pouvez augmenter ou diminuer l’intervalle d’interrogation en fonction des exigences de votre application.</span><span class="sxs-lookup"><span data-stu-id="7273c-174">You can increase or decrease the polling interval based on your application's requirements.</span></span> <span data-ttu-id="7273c-175">Dans l’exemple de code ci-dessous, le `PredictionEnginePool` interroge le modèle stocké à l’URI spécifié toutes les minutes.</span><span class="sxs-lookup"><span data-stu-id="7273c-175">In the code sample below, the `PredictionEnginePool` polls the model stored at the specified URI every minute.</span></span>
>
>```csharp
>services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="create-predict-controller"></a><span data-ttu-id="7273c-176">Créer un contrôleur de prédictions</span><span class="sxs-lookup"><span data-stu-id="7273c-176">Create Predict controller</span></span>

<span data-ttu-id="7273c-177">Pour traiter les requêtes HTTP entrantes, créez un contrôleur.</span><span class="sxs-lookup"><span data-stu-id="7273c-177">To process your incoming HTTP requests, create a controller.</span></span>

1. <span data-ttu-id="7273c-178">Dans l’Explorateur de solutions, cliquez avec le bouton droit sur le répertoire *Contrôleurs*, puis sélectionnez **Ajouter > Contrôleur**.</span><span class="sxs-lookup"><span data-stu-id="7273c-178">In Solution Explorer, right-click the *Controllers* directory, and then select **Add > Controller**.</span></span>
1. <span data-ttu-id="7273c-179">Dans la boîte de dialogue **Ajouter un nouvel élément**, sélectionnez **Contrôleur d’API vide** et **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="7273c-179">In the **Add New Item** dialog box, select **API Controller Empty** and select **Add**.</span></span>
1. <span data-ttu-id="7273c-180">À l’invite, remplacez la valeur du champ **Nom du contrôleur** par *PredictController.cs*.</span><span class="sxs-lookup"><span data-stu-id="7273c-180">In the prompt change the **Controller Name** field to *PredictController.cs*.</span></span> <span data-ttu-id="7273c-181">Ensuite, sélectionnez le bouton Ajouter.</span><span class="sxs-lookup"><span data-stu-id="7273c-181">Then, select the Add button.</span></span> <span data-ttu-id="7273c-182">Le fichier *PredictController.cs* s’ouvre dans l’éditeur de code.</span><span class="sxs-lookup"><span data-stu-id="7273c-182">The *PredictController.cs* file opens in the code editor.</span></span> <span data-ttu-id="7273c-183">Ajoutez l’instruction using suivante en haut du fichier *PredictController.cs* :</span><span class="sxs-lookup"><span data-stu-id="7273c-183">Add the following using statement to the top of *PredictController.cs*:</span></span>

    ```csharp
    using System;
    using Microsoft.AspNetCore.Mvc;
    using Microsoft.Extensions.ML;
    using SentimentAnalysisWebAPI.DataModels;
    ```

    <span data-ttu-id="7273c-184">Supprimez la définition de classe existante et ajoutez le code suivant au fichier *PredictController.cs* :</span><span class="sxs-lookup"><span data-stu-id="7273c-184">Remove the existing class definition and add the following code to the *PredictController.cs* file:</span></span>

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

            SentimentPrediction prediction = _predictionEnginePool.Predict(modelName: "SentimentAnalysisModel", example: input);

            string sentiment = Convert.ToBoolean(prediction.Prediction) ? "Positive" : "Negative";

            return Ok(sentiment);
        }
    }
    ```

<span data-ttu-id="7273c-185">Ce code affecte le `PredictionEnginePool` en le passant au constructeur du contrôleur, obtenu par injection de dépendances.</span><span class="sxs-lookup"><span data-stu-id="7273c-185">This code assigns the `PredictionEnginePool` by passing it to the controller's constructor which you get via dependency injection.</span></span> <span data-ttu-id="7273c-186">Ensuite, la méthode `Post` du contrôleur `Predict` utilise le `PredictionEnginePool` pour effectuer des prédictions à l’aide de la `SentimentAnalysisModel` inscrite dans la classe `Startup` et retourne les résultats à l’utilisateur en cas de réussite.</span><span class="sxs-lookup"><span data-stu-id="7273c-186">Then, the `Predict` controller's `Post` method uses the `PredictionEnginePool` to make predictions using the `SentimentAnalysisModel` registered in the `Startup` class and returns the results back to the user if successful.</span></span>

## <a name="test-web-api-locally"></a><span data-ttu-id="7273c-187">Tester l’API web localement</span><span class="sxs-lookup"><span data-stu-id="7273c-187">Test web API locally</span></span>

<span data-ttu-id="7273c-188">Maintenant que tout est configuré, il est temps de tester l’application.</span><span class="sxs-lookup"><span data-stu-id="7273c-188">Once everything is set up, it's time to test the application.</span></span>

1. <span data-ttu-id="7273c-189">Exécutez l'application.</span><span class="sxs-lookup"><span data-stu-id="7273c-189">Run the application.</span></span>
1. <span data-ttu-id="7273c-190">Ouvrez PowerShell et entrez le code suivant, où PORT est le port d’écoute de votre application.</span><span class="sxs-lookup"><span data-stu-id="7273c-190">Open Powershell and enter the following code where PORT is the port your application is listening on.</span></span>

    ```powershell
    Invoke-RestMethod "https://localhost:<PORT>/api/predict" -Method Post -Body (@{SentimentText="This was a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="7273c-191">En cas de réussite, la sortie devrait se présenter ainsi :</span><span class="sxs-lookup"><span data-stu-id="7273c-191">If successful, the output should look similar to the text below:</span></span>

    ```powershell
    Negative
    ```

<span data-ttu-id="7273c-192">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="7273c-192">Congratulations!</span></span> <span data-ttu-id="7273c-193">Vous avez réussi à alimenter votre modèle de façon à effectuer des prédictions sur Internet à l’aide d’une API web ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="7273c-193">You have successfully served your model to make predictions over the internet using an ASP.NET Core Web API.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7273c-194">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="7273c-194">Next Steps</span></span>

- [<span data-ttu-id="7273c-195">Déployer sur Azure</span><span class="sxs-lookup"><span data-stu-id="7273c-195">Deploy to Azure</span></span>](/aspnet/core/tutorials/publish-to-azure-webapp-using-vs#deploy-the-app-to-azure)
