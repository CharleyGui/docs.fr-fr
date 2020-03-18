---
title: Transformations de données
description: Explorez les composants d’ingénierie de fonctionnalité pris en charge dans ML.NET.
ms.date: 04/02/2019
ms.openlocfilehash: ca410b475c556db5ad4c3862fb79755b455d6830
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79398922"
---
# <a name="data-transformations"></a>Transformations de données

Les transformations de données sont utilisées pour :

- préparer les données pour l’entraînement de modèles
- appliquer un modèle importé au format TensorFlow ou ONNX
- traiter les données après qu’elles ont été transmises par le biais d’un modèle

Les transformations abordées dans ce guide retournent des classes qui implémentent l’interface [IEstimator](xref:Microsoft.ML.IEstimator%601). Les transformations de données peuvent s’enchaîner. Chacune transformation attend et génère des données de type et de format spécifiques, indiqués dans le lien de la documentation de référence.

Certaines transformations de données ont besoin de données d’apprentissage pour calculer leurs paramètres. Par exemple, le transformateur <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> calcule la moyenne et la variance des données d’apprentissage au cours de l’opération `Fit()` et utilise ces paramètres dans l’opération `Transform()`.

D’autres transformations de données n’exigent pas les données d’apprentissage. Par exemple, la transformation <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale%2A> peut effectuer l’opération `Transform()` sans consulter ces données durant l’opération `Fit()`.

## <a name="column-mapping-and-grouping"></a>Mappage et regroupement de colonnes

| Transformer | Définition |
| --- | --- |
| <xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A> | Concaténer une ou plusieurs colonnes d’entrée en une nouvelle colonne de sortie |
| <xref:Microsoft.ML.TransformExtensionsCatalog.CopyColumns%2A> | Copier et renommer une ou plusieurs colonnes d’entrée |
| <xref:Microsoft.ML.TransformExtensionsCatalog.DropColumns%2A> | Supprimer une ou plusieurs colonnes d’entrée |
| <xref:Microsoft.ML.TransformExtensionsCatalog.SelectColumns%2A> | Sélectionner une ou plusieurs colonnes à exclure des données d’entrée |

## <a name="normalization-and-scaling"></a>Normalisation et pondération

| Transformer | Définition |
| --- | --- |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMeanVariance%2A> | Soustraire la moyenne (des données d’apprentissage) et diviser par la variance (des données d’apprentissage) |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLogMeanVariance%2A> | Normaliser selon le logarithme des données d’apprentissage |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeLpNorm%2A> | Mettre à l’échelle des vecteurs d’entrée par leur norme Lp, où p vaut 1, 2 ou l’infini, avec L² (distance euclidienne) comme valeur par défaut |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeGlobalContrast%2A> | Pondérer chacune des valeurs d’une ligne en soustrayant la moyenne des données de la ligne, diviser par l’écart type ou la norme L² (des données de la ligne) et multiplier par un facteur de proportionnalité configurable (par défaut, 2) |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A> | Affecter à la valeur d’entrée un index d’emplacement (bin) et diviser par le nombre d’emplacements pour produire une valeur float comprise entre 0 et 1, les limites étant calculées pour distribuer uniformément les données d’apprentissage dans les emplacements |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeSupervisedBinning%2A> | Affecter à la valeur d’entrée un emplacement en fonction de sa corrélation avec la colonne d’étiquettes |
| <xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A> | Pondérer l’entrée selon la différence entre les valeurs minimales et les valeurs maximales des données d’apprentissage |

## <a name="conversions-between-data-types"></a>Conversions entre types de données

| Transformer | Définition |
| --- | --- |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.ConvertType%2A> | Convertir le type d’une colonne d’entrée en un nouveau type |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValue%2A> | Mapper les valeurs sur les clés (catégories) en fonction du dictionnaire de mappages fourni |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A> | Mapper les valeurs sur les clés (catégories) en créant le mappage à partir des données d’entrée |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A> | Reconvertir les clés dans leurs valeurs d’origine |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToVector%2A> | Reconvertir les clés en vecteurs de valeurs d’origine |
| <xref:Microsoft.ML.ConversionsCatalog.MapKeyToBinaryVector%2A> | Reconvertir les clés en un vecteur binaire de valeurs d’origine |
| <xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A> | Hacher la valeur dans la colonne d’entrée |

## <a name="text-transformations"></a>Transformations textuelles

| Transformer | Définition |
| --- | --- |
| <xref:Microsoft.ML.TextCatalog.FeaturizeText%2A> | Transformer une colonne de texte en un tableau float de nombres de n-grammes et de car-grammes normalisés |
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A> | Fractionner une ou plusieurs colonnes de texte en mots |
| <xref:Microsoft.ML.TextCatalog.TokenizeIntoCharactersAsKeys%2A> | Fractionner une ou plusieurs colonnes de texte en valeurs float de caractères sur un ensemble de rubriques |
| <xref:Microsoft.ML.TextCatalog.NormalizeText%2A> | Modifier la casse, supprimer les signes diacritiques, les signes de ponctuation et les chiffres |
| <xref:Microsoft.ML.TextCatalog.ProduceNgrams%2A> | Transformer une colonne de texte en un sac de nombres de n-grammes (séquences de mots consécutifs)|
| <xref:Microsoft.ML.TextCatalog.ProduceWordBags%2A> | Transformer une colonne de texte en un sac de nombres de vecteur de n-grammes |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedNgrams%2A> | Transformer la colonne de texte en un vecteur de nombres de n-grammes hachés |
| <xref:Microsoft.ML.TextCatalog.ProduceHashedWordBags%2A> | Transformer la colonne de texte en un sac de nombres de n-grammes hachés |
| <xref:Microsoft.ML.TextCatalog.RemoveDefaultStopWords%2A>  | Supprimer les mots vides par défaut des colonnes d’entrée pour la langue spécifiée |
| <xref:Microsoft.ML.TextCatalog.RemoveStopWords%2A> | Supprimer les mots vides spécifiés des colonnes d’entrée |
| <xref:Microsoft.ML.TextCatalog.LatentDirichletAllocation%2A> | Transformer un document (représenté sous la forme d’un vecteur de valeurs float) en un vecteur de valeurs float sur un ensemble de rubriques |
| <xref:Microsoft.ML.TextCatalog.ApplyWordEmbedding%2A> | Convertir des vecteurs de jetons textuels en vecteurs de phrases selon un modèle préentraîné |

## <a name="image-transformations"></a>Transformations d’images

| Transformer | Définition |
| --- | --- |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToGrayscale%2A> | Convertir une image en nuances de gris |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ConvertToImage%2A> | Convertir un vecteur de pixels en <xref:Microsoft.ML.Transforms.Image.ImageDataViewType> |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ExtractPixels%2A> | Convertir les pixels d’une image d’entrée en un vecteur de nombres |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.LoadImages%2A> | Charger les images d’un dossier en mémoire |
| <xref:Microsoft.ML.ImageEstimatorsCatalog.ResizeImages%2A> | Redimensionner les images |
| <xref:Microsoft.ML.OnnxCatalog.DnnFeaturizeImage%2A> | Appliquer un modèle DNN (Deep Neural Network) préentraîné pour transformer une image d’entrée en un vecteur de fonctionnalité |

## <a name="categorical-data-transformations"></a>Transformations de données catégoriques

| Transformer | Définition |
| --- | --- |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A> | Convertir une ou plusieurs colonnes de texte en vecteurs encodés [one-hot](https://en.wikipedia.org/wiki/One-hot) |
| <xref:Microsoft.ML.CategoricalCatalog.OneHotHashEncoding%2A> | Convertir une ou plusieurs colonnes de texte en vecteurs encodés one-hot par hachage |

## <a name="time-series-data-transformations"></a>Transformations de données de séries chronologiques

| Transformer | Définition |
| --- | --- |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectAnomalyBySrCnn%2A> | Détecter les anomalies dans les données de séries chronologiques d’entrée à l’aide de l’algorithme SR (Spectral Residual) |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectChangePointBySsa%2A> | Détecter les points de changement dans les données de séries chronologiques à l’aide de l’analyse de spectre singulier (SSA) |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectIidChangePoint%2A> | Détecter les points de changement dans des données de séries chronologiques indépendantes et identiquement distribuées à l’aide d’estimations de densité de noyau adaptative et de scores martingales |
| <xref:Microsoft.ML.TimeSeriesCatalog.ForecastBySsa%2A> | Prévoir des données de séries chronologiques à l’aide de l’analyse de spectre singulier (SSA) |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectSpikeBySsa%2A> | Détecter les pics dans les données de séries chronologiques à l’aide de l’analyse de spectre singulier (SSA) |
| <xref:Microsoft.ML.TimeSeriesCatalog.DetectIidSpike%2A> | Détecter les pics dans des données de séries chronologiques indépendantes et identiquement distribuées à l’aide d’estimations de densité de noyau adaptative et de scores martingales |

## <a name="missing-values"></a>Valeurs manquantes

| Transformer | Définition |
| --- | --- |
| <xref:Microsoft.ML.ExtensionsCatalog.IndicateMissingValues%2A> | Créer une colonne de sortie booléenne dont la valeur est true s’il manque la valeur de la colonne d’entrée |
| <xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A> | Créer une colonne de sortie dont la valeur est définie sur une valeur par défaut s’il manque la valeur de la colonne d’entrée, sur la valeur d’entrée sinon |

## <a name="feature-selection"></a>Sélection de caractéristiques

| Transformer | Définition |
| --- | --- |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnCount%2A> | Sélectionner les caractéristiques dont les valeurs par défaut sont supérieures à un seuil |
| <xref:Microsoft.ML.FeatureSelectionCatalog.SelectFeaturesBasedOnMutualInformation%2A> | Sélectionnez les caractéristiques dont les données de la colonne d’étiquette dépendent le plus |

## <a name="feature-transformations"></a>Transformations de fonctionnalités

| Transformer | Définition |
| --- | --- |
| <xref:Microsoft.ML.KernelExpansionCatalog.ApproximatedKernelMap%2A> | Mapper chaque vecteur d’entrée à un espace de fonctionnalité dimensionnelle inférieur, où les produits internes se rapprochent d’une fonction de noyau, afin que les fonctionnalités puissent être utilisées comme entrées des algorithmes linéaires |
| <xref:Microsoft.ML.PcaCatalog.ProjectToPrincipalComponents%2A> | Réduire les dimensions du vecteur de fonctionnalité d’entrée en appliquant l’algorithme Principal Component Analysis (PCA) |

## <a name="explainability-transformations"></a>Transformations d’explicabilité

| Transformer | Définition |
| --- | --- |
| <xref:Microsoft.ML.ExplainabilityCatalog.CalculateFeatureContribution%2A> | Calculer les scores de contribution pour chaque élément d’un vecteur de fonctionnalité |

## <a name="calibration-transformations"></a>Transformations d’étalonnage

| Transformer | Définition |
| --- | --- |
|<xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Platt%28System.String%2CSystem.String%2CSystem.String%29> | Transforme un score brut de classifieur binaire en une probabilité de classe à l’aide de la régression logistique avec les paramètres estimés à l’aide des données d’entraînement |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Platt%28System.Double%2CSystem.Double%2CSystem.String%29> | Transforme un score brut de classifieur binaire en une probabilité de classe à l’aide de la régression logistique avec les paramètres fixes |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Naive%2A> | Transforme un score brut de classifieur binaire en une probabilité de classe en affectant des scores à des emplacements et en calculant la probabilité en fonction de la répartition entre les emplacements |
| <xref:Microsoft.ML.BinaryClassificationCatalog.CalibratorsCatalog.Isotonic%2A> | Transforme un score brut de classifieur binaire en une probabilité de classe en affectant des scores à des emplacements, où la position des limites et la taille des emplacements sont estimées à l’aide des données d’entraînement  |

## <a name="deep-learning-transformations"></a>Transformations d’apprentissage profond

| Transformer | Définition |
| --- | --- |
| <xref:Microsoft.ML.OnnxCatalog.ApplyOnnxModel%2A> | Transformer les données d’entrée avec un modèle ONNX importé |
| <xref:Microsoft.ML.TensorflowCatalog.LoadTensorFlowModel%2A> | Transformer les données d’entrée avec un modèle TensorFlow importé |

## <a name="custom-transformations"></a>Transformations personnalisées

| Transformer | Définition |
| --- | --- |
| <xref:Microsoft.ML.CustomMappingCatalog.CustomMapping%2A> | Transformer des colonnes existantes en de nouvelles colonnes suivant un mappage défini par l’utilisateur |
