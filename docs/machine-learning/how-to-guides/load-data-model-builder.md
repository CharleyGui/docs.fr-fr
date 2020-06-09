---
title: Charger les données d’apprentissage pour le générateur de modèles
description: Découvrez comment charger des données d’apprentissage à partir d’une base de données SQL Server ou d’un fichier pour les utiliser dans l’un des scénarios de générateur de modèles pour ML.NET.
ms.date: 10/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, mlnet-tooling
ms.openlocfilehash: 64e366b3c66427ccd2810324abeb880f6cb9ebc1
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602204"
---
# <a name="load-training-data-into-model-builder"></a><span data-ttu-id="802e4-103">Charger les données d’apprentissage dans le générateur de modèles</span><span class="sxs-lookup"><span data-stu-id="802e4-103">Load training data into Model Builder</span></span>

<span data-ttu-id="802e4-104">Découvrez comment charger vos jeux de données d’apprentissage à partir d’un fichier ou d’une base de données SQL Server pour une utilisation dans l’un des scénarios de générateur de modèles pour ML.NET.</span><span class="sxs-lookup"><span data-stu-id="802e4-104">Learn how to load your training datasets from a file or a SQL Server database for use in one of the Model Builder scenarios for ML.NET.</span></span> <span data-ttu-id="802e4-105">Les scénarios de générateur de modèles peuvent utiliser des SQL Server des bases de données, des fichiers image et des formats de fichier CSV ou TSV en tant que données d’apprentissage.</span><span class="sxs-lookup"><span data-stu-id="802e4-105">Model Builder scenarios can use SQL Server databases, image files, and CSV or TSV file formats as training data.</span></span>

## <a name="training-dataset-limitations-in-model-builder"></a><span data-ttu-id="802e4-106">Limitations des jeux de données de formation dans le générateur de modèles</span><span class="sxs-lookup"><span data-stu-id="802e4-106">Training dataset limitations in Model Builder</span></span>

<span data-ttu-id="802e4-107">Le générateur de modèles limite la quantité et le type de données que vous pouvez utiliser pour les modèles d’apprentissage :</span><span class="sxs-lookup"><span data-stu-id="802e4-107">Model Builder limits the amount and type of data you can use for training models:</span></span>

- <span data-ttu-id="802e4-108">SQL Server données : 100 000 lignes</span><span class="sxs-lookup"><span data-stu-id="802e4-108">SQL Server data: 100,000 rows</span></span>
- <span data-ttu-id="802e4-109">Fichiers CSV et TSV : aucune limite de taille</span><span class="sxs-lookup"><span data-stu-id="802e4-109">CSV and TSV files: No size limit</span></span>
- <span data-ttu-id="802e4-110">Images : PNG et JPG uniquement.</span><span class="sxs-lookup"><span data-stu-id="802e4-110">Images: PNG and JPG only.</span></span>

## <a name="model-builder-scenarios"></a><span data-ttu-id="802e4-111">Scénarios de générateur de modèles</span><span class="sxs-lookup"><span data-stu-id="802e4-111">Model Builder scenarios</span></span>

<span data-ttu-id="802e4-112">Le générateur de modèles vous permet de créer des modèles pour les scénarios de Machine Learning suivants :</span><span class="sxs-lookup"><span data-stu-id="802e4-112">Model Builder helps you create models for the following machine learning scenarios:</span></span>

- <span data-ttu-id="802e4-113">Analyse des sentiments (classification binaire) : classifier les données textuelles en deux catégories.</span><span class="sxs-lookup"><span data-stu-id="802e4-113">Sentiment analysis (binary classification): Classify textual data into two categories.</span></span>
- <span data-ttu-id="802e4-114">Classification des problèmes (classification multiclasse) : classifier les données textuelles en 3 catégories ou plus.</span><span class="sxs-lookup"><span data-stu-id="802e4-114">Issue classification (multiclass classification): Classify textual data into 3 or more categories.</span></span>
- <span data-ttu-id="802e4-115">Prédiction de prix (régression) : prédire une valeur numérique.</span><span class="sxs-lookup"><span data-stu-id="802e4-115">Price prediction (regression): Predict a numeric value.</span></span>
- <span data-ttu-id="802e4-116">Classification des images (apprentissage profond) : classer les images en fonction des caractéristiques.</span><span class="sxs-lookup"><span data-stu-id="802e4-116">Image classification (deep learning): Categorize images based on characteristics.</span></span>
- <span data-ttu-id="802e4-117">Scénario personnalisé : créez des scénarios personnalisés à partir de vos données à l’aide de la régression, de la classification et d’autres tâches.</span><span class="sxs-lookup"><span data-stu-id="802e4-117">Custom scenario: Build custom scenarios from your data using regression, classification, and other tasks.</span></span>

<span data-ttu-id="802e4-118">Cet article traite des scénarios de classification et de régression avec des données textuelles ou numériques, ainsi que des scénarios de classification d’images.</span><span class="sxs-lookup"><span data-stu-id="802e4-118">This article covers classification and regression scenarios with textual or numerical data, and image classification scenarios.</span></span>

## <a name="load-text-or-numeric-data-from-a-file"></a><span data-ttu-id="802e4-119">Charger du texte ou des données numériques à partir d’un fichier</span><span class="sxs-lookup"><span data-stu-id="802e4-119">Load text or numeric data from a file</span></span>

<span data-ttu-id="802e4-120">Vous pouvez charger du texte ou des données numériques d’un fichier dans le générateur de modèles.</span><span class="sxs-lookup"><span data-stu-id="802e4-120">You can load text or numeric data from a file into Model Builder.</span></span> <span data-ttu-id="802e4-121">Il accepte les formats de fichiers CSV (délimité par des virgules) ou TSV (délimité par des tabulations).</span><span class="sxs-lookup"><span data-stu-id="802e4-121">It accepts comma-delimited (CSV) or tab-delimited (TSV) file formats.</span></span>

1. <span data-ttu-id="802e4-122">À l’étape données du générateur de modèles, sélectionnez **fichier** dans la liste déroulante source de données.</span><span class="sxs-lookup"><span data-stu-id="802e4-122">In the data step of Model Builder, select **File** from the data source dropdown.</span></span>
2. <span data-ttu-id="802e4-123">Sélectionnez le bouton en regard de la zone de texte **Sélectionner un fichier** , puis utilisez l’Explorateur de fichiers pour parcourir et sélectionner le fichier de données.</span><span class="sxs-lookup"><span data-stu-id="802e4-123">Select the button next to the **Select a file** text box, and use File Explorer to browse and select the data file.</span></span>
3. <span data-ttu-id="802e4-124">Choisissez une catégorie dans la liste déroulante **colonne à prédire (étiquette)** .</span><span class="sxs-lookup"><span data-stu-id="802e4-124">Choose a category in the **Column to Predict (Label)** dropdown.</span></span>
4. <span data-ttu-id="802e4-125">Dans la liste déroulante **colonnes d’entrée (fonctionnalités)** , vérifiez que les colonnes de données que vous souhaitez inclure sont cochées.</span><span class="sxs-lookup"><span data-stu-id="802e4-125">From the **Input Columns (Features)** dropdown, confirm the data columns you want to include are checked.</span></span>

<span data-ttu-id="802e4-126">Vous avez terminé la configuration de votre fichier de source de données pour le générateur de modèles.</span><span class="sxs-lookup"><span data-stu-id="802e4-126">You're done setting up your data source file for Model Builder.</span></span> <span data-ttu-id="802e4-127">Sélectionnez le lien **train** pour passer à l’étape suivante dans le générateur de modèles.</span><span class="sxs-lookup"><span data-stu-id="802e4-127">Select the **Train** link to move to the next step in Model Builder.</span></span>

## <a name="load-data-from-a-sql-server-database"></a><span data-ttu-id="802e4-128">Charger des données à partir d’une base de données SQL Server</span><span class="sxs-lookup"><span data-stu-id="802e4-128">Load data from a SQL Server database</span></span>

<span data-ttu-id="802e4-129">Le générateur de modèles prend en charge le chargement de données à partir de bases de données locales et distantes SQL Server.</span><span class="sxs-lookup"><span data-stu-id="802e4-129">Model Builder supports loading data from local and remote SQL Server databases.</span></span>

<span data-ttu-id="802e4-130">Pour charger des données à partir d’une base de données SQL Server dans module Builder :</span><span class="sxs-lookup"><span data-stu-id="802e4-130">To load data from a SQL Server database into Module Builder:</span></span>

1. <span data-ttu-id="802e4-131">À l’étape données du générateur de modèles, sélectionnez **SQL Server** dans la liste déroulante source de données.</span><span class="sxs-lookup"><span data-stu-id="802e4-131">In the data step of Model Builder, select **SQL Server** from the data source dropdown.</span></span>
1. <span data-ttu-id="802e4-132">Sélectionnez le bouton en regard de la zone **de texte connexion à SQL Server base de données** .</span><span class="sxs-lookup"><span data-stu-id="802e4-132">Select the button next to the **Connect to SQL Server database** text box.</span></span>
    1. <span data-ttu-id="802e4-133">Dans la boîte de dialogue **choisir des données** , sélectionnez **Microsoft SQL Server fichier de base de données**.</span><span class="sxs-lookup"><span data-stu-id="802e4-133">In the **Choose Data** dialog, select **Microsoft SQL Server Database File**.</span></span>
    1. <span data-ttu-id="802e4-134">Décochez la case **toujours utiliser cette sélection** et sélectionnez **Continuer**</span><span class="sxs-lookup"><span data-stu-id="802e4-134">Uncheck the **Always use this selection** checkbox and select **Continue**</span></span>
    1. <span data-ttu-id="802e4-135">Dans la boîte de dialogue **Propriétés de connexion** , sélectionnez **Parcourir** et sélectionnez le téléchargé. Fichier MDF.</span><span class="sxs-lookup"><span data-stu-id="802e4-135">In the **Connection Properties** dialog, select **Browse** and select the downloaded .MDF file.</span></span>
    1. <span data-ttu-id="802e4-136">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="802e4-136">Select **OK**</span></span>
1. <span data-ttu-id="802e4-137">Choisissez le nom du DataSet dans la liste déroulante nom de la **table** .</span><span class="sxs-lookup"><span data-stu-id="802e4-137">Choose the dataset name from the **Table Name** dropdown.</span></span>
1. <span data-ttu-id="802e4-138">Dans la liste déroulante **colonne à prédire (étiquette)** , choisissez la catégorie de données sur laquelle vous souhaitez effectuer une prédiction.</span><span class="sxs-lookup"><span data-stu-id="802e4-138">From the **Column to Predict (Label)** dropdown, choose the data category on which you want to make a prediction.</span></span>
1. <span data-ttu-id="802e4-139">Dans la liste déroulante **colonnes d’entrée (fonctionnalités)** , vérifiez que les colonnes que vous souhaitez inclure sont cochées.</span><span class="sxs-lookup"><span data-stu-id="802e4-139">From the **Input Columns (Features)** dropdown, confirm the columns you want to include are checked.</span></span>

<span data-ttu-id="802e4-140">Vous avez terminé la configuration de votre fichier de source de données pour le générateur de modèles.</span><span class="sxs-lookup"><span data-stu-id="802e4-140">You're done setting up your data source file for Model Builder.</span></span> <span data-ttu-id="802e4-141">Sélectionnez le lien **train** pour passer à l’étape suivante dans le générateur de modèles.</span><span class="sxs-lookup"><span data-stu-id="802e4-141">Select the **Train** link to move to the next step in Model Builder.</span></span>

## <a name="set-up-image-data-files"></a><span data-ttu-id="802e4-142">Configurer des fichiers de données image</span><span class="sxs-lookup"><span data-stu-id="802e4-142">Set up image data files</span></span>

<span data-ttu-id="802e4-143">Le générateur de modèles s’attend à ce que les données de l’image soient des fichiers JPG ou PNG organisés dans des dossiers qui correspondent aux catégories de la classification.</span><span class="sxs-lookup"><span data-stu-id="802e4-143">Model Builder expects image data to be JPG or PNG files organized in folders that correspond to the categories of the classification.</span></span>

<span data-ttu-id="802e4-144">Pour charger des images dans le générateur de modèles, indiquez le chemin d’accès à un répertoire de niveau supérieur unique :</span><span class="sxs-lookup"><span data-stu-id="802e4-144">To load images into Model Builder, provide the path to a single top-level directory:</span></span>

- <span data-ttu-id="802e4-145">Ce répertoire de niveau supérieur contient un sous-dossier pour chacune des catégories à prédire.</span><span class="sxs-lookup"><span data-stu-id="802e4-145">This top-level directory contains one subfolder for each of the categories to predict.</span></span>
- <span data-ttu-id="802e4-146">Chaque sous-dossier contient les fichiers image appartenant à sa catégorie.</span><span class="sxs-lookup"><span data-stu-id="802e4-146">Each subfolder contains the image files belonging to its category.</span></span>

<span data-ttu-id="802e4-147">Dans la structure de dossiers illustrée ci-dessous, le répertoire de niveau supérieur est *flower_photos*.</span><span class="sxs-lookup"><span data-stu-id="802e4-147">In the folder structure illustrated below, the top-level directory is *flower_photos*.</span></span> <span data-ttu-id="802e4-148">Il y a cinq sous-répertoires correspondant aux catégories que vous souhaitez prédire : marguerites, dandelion, roses, tournesols et tulipes.</span><span class="sxs-lookup"><span data-stu-id="802e4-148">There are five subdirectories corresponding to the categories you want to predict: daisy, dandelion, roses, sunflowers, and tulips.</span></span> <span data-ttu-id="802e4-149">Chacun de ces sous-répertoires contient des images appartenant à sa catégorie respective.</span><span class="sxs-lookup"><span data-stu-id="802e4-149">Each of these subdirectories contains images belonging to its respective category.</span></span>

```text
\---flower_photos
    +---daisy
    |       100080576_f52e8ee070_n.jpg
    |       102841525_bd6628ae3c.jpg
    |       105806915_a9c13e2106_n.jpg
    |
    +---dandelion
    |       10443973_aeb97513fc_m.jpg
    |       10683189_bd6e371b97.jpg
    |       10919961_0af657c4e8.jpg
    |
    +---roses
    |       102501987_3cdb8e5394_n.jpg
    |       110472418_87b6a3aa98_m.jpg
    |       118974357_0faa23cce9_n.jpg
    |
    +---sunflowers
    |       127192624_afa3d9cb84.jpg
    |       145303599_2627e23815_n.jpg
    |       147804446_ef9244c8ce_m.jpg
    |
    \---tulips
            100930342_92e8746431_n.jpg
            107693873_86021ac4ea_n.jpg
            10791227_7168491604.jpg
```

## <a name="next-steps"></a><span data-ttu-id="802e4-150">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="802e4-150">Next steps</span></span>

<span data-ttu-id="802e4-151">Suivez ces didacticiels pour créer des applications Machine Learning avec le générateur de modèles :</span><span class="sxs-lookup"><span data-stu-id="802e4-151">Follow these tutorials to build machine learning apps with Model Builder:</span></span>

- [<span data-ttu-id="802e4-152">Prédire des prix à l’aide de la régression</span><span class="sxs-lookup"><span data-stu-id="802e4-152">Predict prices using regression</span></span>](../tutorials/predict-prices-with-model-builder.md)
- [<span data-ttu-id="802e4-153">Analyser les sentiments dans une application Web à l’aide de la classification binaire</span><span class="sxs-lookup"><span data-stu-id="802e4-153">Analyze sentiment in a web application using binary classification</span></span>](../tutorials/sentiment-analysis-model-builder.md)

<span data-ttu-id="802e4-154">Si vous effectuez l’apprentissage d’un modèle à l’aide de code, [Découvrez comment charger des données à l’aide de l’API ml.net](load-data-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="802e4-154">If you're training a model using code, [learn how to load data using the ML.NET API](load-data-ml-net.md).</span></span>
