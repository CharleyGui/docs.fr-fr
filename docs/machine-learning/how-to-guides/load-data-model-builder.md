---
title: Données de formation de charge pour Model Builder
description: Découvrez comment charger les données de formation à partir d’une base de données SQL Server ou d’un fichier à utiliser dans l’un des scénarios Model Builder pour ML.NET.
ms.date: 10/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, mlnet-tooling
ms.openlocfilehash: 23de2d06090f4c1eaa2c79178ba4c346698d45e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78849157"
---
# <a name="load-training-data-into-model-builder"></a><span data-ttu-id="f2444-103">Charger les données de formation dans Model Builder</span><span class="sxs-lookup"><span data-stu-id="f2444-103">Load training data into Model Builder</span></span>

<span data-ttu-id="f2444-104">Découvrez comment charger vos jeux de données de formation à partir d’un fichier ou d’une base de données SQL Server pour une utilisation dans l’un des scénarios Model Builder pour ML.NET.</span><span class="sxs-lookup"><span data-stu-id="f2444-104">Learn how to load your training datasets from a file or a SQL Server database for use in one of the Model Builder scenarios for ML.NET.</span></span> <span data-ttu-id="f2444-105">Les scénarios Model Builder peuvent utiliser les bases de données SQL Server, les fichiers d’images et les formats de fichiers CSV ou TSV comme données de formation.</span><span class="sxs-lookup"><span data-stu-id="f2444-105">Model Builder scenarios can use SQL Server databases, image files, and CSV or TSV file formats as training data.</span></span>

## <a name="training-dataset-limitations-in-model-builder"></a><span data-ttu-id="f2444-106">Limitations de jeu de données de formation dans Le constructeur modèle</span><span class="sxs-lookup"><span data-stu-id="f2444-106">Training dataset limitations in Model Builder</span></span>

<span data-ttu-id="f2444-107">Modèle Builder limite la quantité et le type de données que vous pouvez utiliser pour les modèles de formation :</span><span class="sxs-lookup"><span data-stu-id="f2444-107">Model Builder limits the amount and type of data you can use for training models:</span></span>

- <span data-ttu-id="f2444-108">Données SQL Server : 100 000 lignes</span><span class="sxs-lookup"><span data-stu-id="f2444-108">SQL Server data: 100,000 rows</span></span>
- <span data-ttu-id="f2444-109">Fichiers CSV et TSV : aucune limite de taille</span><span class="sxs-lookup"><span data-stu-id="f2444-109">CSV and TSV files: No size limit</span></span>
- <span data-ttu-id="f2444-110">Images: PNG et JPG seulement.</span><span class="sxs-lookup"><span data-stu-id="f2444-110">Images: PNG and JPG only.</span></span>

## <a name="model-builder-scenarios"></a><span data-ttu-id="f2444-111">Scénarios De constructeur de modèles</span><span class="sxs-lookup"><span data-stu-id="f2444-111">Model Builder scenarios</span></span>

<span data-ttu-id="f2444-112">Model Builder vous aide à créer des modèles pour les scénarios d’apprentissage automatique suivants :</span><span class="sxs-lookup"><span data-stu-id="f2444-112">Model Builder helps you create models for the following machine learning scenarios:</span></span>

- <span data-ttu-id="f2444-113">Analyse du sentiment (classification binaire) : Classer les données textuelles en deux catégories.</span><span class="sxs-lookup"><span data-stu-id="f2444-113">Sentiment analysis (binary classification): Classify textual data into two categories.</span></span>
- <span data-ttu-id="f2444-114">Classification des questions (classification multiclasse) : Classer les données textuelles en 3 catégories ou plus.</span><span class="sxs-lookup"><span data-stu-id="f2444-114">Issue classification (multiclass classification): Classify textual data into 3 or more categories.</span></span>
- <span data-ttu-id="f2444-115">Prévision des prix (régression) : Prédire une valeur numérique.</span><span class="sxs-lookup"><span data-stu-id="f2444-115">Price prediction (regression): Predict a numeric value.</span></span>
- <span data-ttu-id="f2444-116">Classification des images (apprentissage profond) : Catégoriser les images en fonction des caractéristiques.</span><span class="sxs-lookup"><span data-stu-id="f2444-116">Image classification (deep learning): Categorize images based on characteristics.</span></span>
- <span data-ttu-id="f2444-117">Scénario personnalisé : Construisez des scénarios personnalisés à partir de vos données à l’aide de la régression, de la classification et d’autres tâches.</span><span class="sxs-lookup"><span data-stu-id="f2444-117">Custom scenario: Build custom scenarios from your data using regression, classification, and other tasks.</span></span>

<span data-ttu-id="f2444-118">Cet article couvre les scénarios de classification et de régression avec des données textuelles ou numériques, ainsi que des scénarios de classification d’images.</span><span class="sxs-lookup"><span data-stu-id="f2444-118">This article covers classification and regression scenarios with textual or numerical data, and image classification scenarios.</span></span>

## <a name="load-text-or-numeric-data-from-a-file"></a><span data-ttu-id="f2444-119">Charger le texte ou les données numériques d’un fichier</span><span class="sxs-lookup"><span data-stu-id="f2444-119">Load text or numeric data from a file</span></span>

<span data-ttu-id="f2444-120">Vous pouvez charger des données textuelles ou numériques à partir d’un fichier dans Model Builder.</span><span class="sxs-lookup"><span data-stu-id="f2444-120">You can load text or numeric data from a file into Model Builder.</span></span> <span data-ttu-id="f2444-121">Il accepte les formats de fichiers délimités par virgule (CSV) ou délimités par onglet (TSV).</span><span class="sxs-lookup"><span data-stu-id="f2444-121">It accepts comma-delimited (CSV) or tab-delimited (TSV) file formats.</span></span>

1. <span data-ttu-id="f2444-122">Dans l’étape de données de Model Builder, sélectionnez **Fichier** à partir de la baisse de la source de données.</span><span class="sxs-lookup"><span data-stu-id="f2444-122">In the data step of Model Builder, select **File** from the data source dropdown.</span></span>
2. <span data-ttu-id="f2444-123">Sélectionnez le bouton à côté de la boîte de texte **Select,** et utilisez File Explorer pour parcourir et sélectionner le fichier de données.</span><span class="sxs-lookup"><span data-stu-id="f2444-123">Select the button next to the **Select a file** text box, and use File Explorer to browse and select the data file.</span></span>
3. <span data-ttu-id="f2444-124">Choisissez une catégorie dans la **colonne pour prédire (label)** dropdown.</span><span class="sxs-lookup"><span data-stu-id="f2444-124">Choose a category in the **Column to Predict (Label)** dropdown.</span></span>
4. <span data-ttu-id="f2444-125">À partir du décrochage **des colonnes d’entrée (Caractéristiques),** confirmez que les colonnes de données que vous souhaitez inclure sont vérifiées.</span><span class="sxs-lookup"><span data-stu-id="f2444-125">From the **Input Columns (Features)** dropdown, confirm the data columns you want to include are checked.</span></span>

<span data-ttu-id="f2444-126">Vous avez terminé la mise en place de votre fichier source de données pour Model Builder.</span><span class="sxs-lookup"><span data-stu-id="f2444-126">You're done setting up your data source file for Model Builder.</span></span> <span data-ttu-id="f2444-127">Sélectionnez le lien **Train** pour passer à l’étape suivante dans Model Builder.</span><span class="sxs-lookup"><span data-stu-id="f2444-127">Select the **Train** link to move to the next step in Model Builder.</span></span>

## <a name="load-data-from-a-sql-server-database"></a><span data-ttu-id="f2444-128">Chargez les données d’une base de données SQL Server</span><span class="sxs-lookup"><span data-stu-id="f2444-128">Load data from a SQL Server database</span></span>

<span data-ttu-id="f2444-129">Model Builder prend en charge le chargement des données des bases de données LOCALEs et éloignées DE SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f2444-129">Model Builder supports loading data from local and remote SQL Server databases.</span></span>

<span data-ttu-id="f2444-130">Pour charger les données d’une base de données SQL Server dans Module Builder :</span><span class="sxs-lookup"><span data-stu-id="f2444-130">To load data from a SQL Server database into Module Builder:</span></span>

1. <span data-ttu-id="f2444-131">Dans l’étape de données de Model Builder, sélectionnez **SQL Server** à partir de la source de données.</span><span class="sxs-lookup"><span data-stu-id="f2444-131">In the data step of Model Builder, select **SQL Server** from the data source dropdown.</span></span>
1. <span data-ttu-id="f2444-132">Sélectionnez le bouton à côté de la boîte **texte de base de données Connect to SQL Server.**</span><span class="sxs-lookup"><span data-stu-id="f2444-132">Select the button next to the **Connect to SQL Server database** text box.</span></span>
    1. <span data-ttu-id="f2444-133">Dans le dialogue **Choisissez les données,** sélectionnez **Microsoft SQL Server Database File**.</span><span class="sxs-lookup"><span data-stu-id="f2444-133">In the **Choose Data** dialog, select **Microsoft SQL Server Database File**.</span></span>
    1. <span data-ttu-id="f2444-134">Décochez **la toujours utiliser cette** boîte à cocher de sélection et sélectionnez **Continuer**</span><span class="sxs-lookup"><span data-stu-id="f2444-134">Uncheck the **Always use this selection** checkbox and select **Continue**</span></span>
    1. <span data-ttu-id="f2444-135">Dans le dialogue **Connection Properties,** **sélectionnez Browse** et sélectionnez les téléchargements . Fichier MDF.</span><span class="sxs-lookup"><span data-stu-id="f2444-135">In the **Connection Properties** dialog, select **Browse** and select the downloaded .MDF file.</span></span>
    1. <span data-ttu-id="f2444-136">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="f2444-136">Select **OK**</span></span>
1. <span data-ttu-id="f2444-137">Choisissez le nom de jeu de données de la décroche du nom de **table.**</span><span class="sxs-lookup"><span data-stu-id="f2444-137">Choose the dataset name from the **Table Name** dropdown.</span></span>
1. <span data-ttu-id="f2444-138">De la **colonne à prédire (label)** dropdown, choisissez la catégorie de données sur laquelle vous souhaitez faire une prédiction.</span><span class="sxs-lookup"><span data-stu-id="f2444-138">From the **Column to Predict (Label)** dropdown, choose the data category on which you want to make a prediction.</span></span>
1. <span data-ttu-id="f2444-139">À partir du décrochage **des colonnes d’entrée (Caractéristiques),** confirmez les colonnes que vous souhaitez inclure sont vérifiées.</span><span class="sxs-lookup"><span data-stu-id="f2444-139">From the **Input Columns (Features)** dropdown, confirm the columns you want to include are checked.</span></span>

<span data-ttu-id="f2444-140">Vous avez terminé la mise en place de votre fichier source de données pour Model Builder.</span><span class="sxs-lookup"><span data-stu-id="f2444-140">You're done setting up your data source file for Model Builder.</span></span> <span data-ttu-id="f2444-141">Sélectionnez le lien **Train** pour passer à l’étape suivante dans Model Builder.</span><span class="sxs-lookup"><span data-stu-id="f2444-141">Select the **Train** link to move to the next step in Model Builder.</span></span>

## <a name="set-up-image-data-files"></a><span data-ttu-id="f2444-142">Configurer des fichiers de données d’image</span><span class="sxs-lookup"><span data-stu-id="f2444-142">Set up image data files</span></span>

<span data-ttu-id="f2444-143">Model Builder s’attend à ce que les données d’image soient des fichiers JPG ou PNG organisés dans des dossiers correspondant aux catégories de la classification.</span><span class="sxs-lookup"><span data-stu-id="f2444-143">Model Builder expects image data to be JPG or PNG files organized in folders that correspond to the categories of the classification.</span></span>

<span data-ttu-id="f2444-144">Pour charger des images dans Model Builder, offrez le chemin vers un répertoire de haut niveau unique :</span><span class="sxs-lookup"><span data-stu-id="f2444-144">To load images into Model Builder, provide the path to a single top-level directory:</span></span>

- <span data-ttu-id="f2444-145">Ce répertoire de haut niveau contient un sous-pli pour chacune des catégories à prévoir.</span><span class="sxs-lookup"><span data-stu-id="f2444-145">This top-level directory contains one subfolder for each of the categories to predict.</span></span>
- <span data-ttu-id="f2444-146">Chaque sous-pliage contient les fichiers d’image appartenant à sa catégorie.</span><span class="sxs-lookup"><span data-stu-id="f2444-146">Each subfolder contains the image files belonging to its category.</span></span>

<span data-ttu-id="f2444-147">Dans la structure du dossier illustrée ci-dessous, le répertoire de haut niveau est *flower_photos*.</span><span class="sxs-lookup"><span data-stu-id="f2444-147">In the folder structure illustrated below, the top-level directory is *flower_photos*.</span></span> <span data-ttu-id="f2444-148">Il y a cinq sous-directeurs correspondant aux catégories que vous voulez prédire : marguerite, pissenlit, roses, tournesols et tulipes.</span><span class="sxs-lookup"><span data-stu-id="f2444-148">There are five subdirectories corresponding to the categories you want to predict: daisy, dandelion, roses, sunflowers, and tulips.</span></span> <span data-ttu-id="f2444-149">Chacune de ces sous-directions contient des images appartenant à sa catégorie respective.</span><span class="sxs-lookup"><span data-stu-id="f2444-149">Each of these subdirectories contains images belonging to its respective category.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="f2444-150">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="f2444-150">Next steps</span></span>

<span data-ttu-id="f2444-151">Suivez ces tutoriels pour créer des applications d’apprentissage automatique avec Model Builder :</span><span class="sxs-lookup"><span data-stu-id="f2444-151">Follow these tutorials to build machine learning apps with Model Builder:</span></span>

- [<span data-ttu-id="f2444-152">Prédire des prix à l’aide de la régression</span><span class="sxs-lookup"><span data-stu-id="f2444-152">Predict prices using regression</span></span>](../tutorials/predict-prices-with-model-builder.md)
- [<span data-ttu-id="f2444-153">Analyser le sentiment dans une application web à l’aide de la classification binaire</span><span class="sxs-lookup"><span data-stu-id="f2444-153">Analyze sentiment in a web application using binary classification</span></span>](../tutorials/sentiment-analysis-model-builder.md )

<span data-ttu-id="f2444-154">Si vous entraînez un modèle à l’aide de code, [apprenez à charger des données à l’aide de l’API ML.NET](load-data-ml-net.md).</span><span class="sxs-lookup"><span data-stu-id="f2444-154">If you're training a model using code, [learn how to load data using the ML.NET API](load-data-ml-net.md).</span></span>
