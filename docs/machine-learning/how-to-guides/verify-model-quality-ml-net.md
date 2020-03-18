---
title: Calculer des métriques pour évaluer la qualité du modèle Machine Learning
description: Découvrez comment calculer des métriques pour évaluer et vérifier la qualité du modèle Machine Learning avec ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: d6409307cd283ae67d7546c4dc6e19e6089a0766
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73975842"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality"></a>Calculer des métriques pour évaluer la qualité du modèle Machine Learning

> [!NOTE]
> Cette rubrique fait référence à ML.NET, actuellement en préversion, et les ressources sont susceptibles d’être modifiées. Pour plus d’informations, visitez la page [ML.NET.](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet)

Ce guide pratique et l’exemple associé utilisent actuellement **ML.NET version 0.10**. Pour plus d’informations, voir les notes de publication dans le référentiel GitHub [dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

Comment évaluer la qualité après avoir entraîné le modèle ? Chaque tâche de machine learning expose des métriques pour l’évaluation de la qualité.

Vous pouvez utiliser le « contexte » correspondant de la tâche pour évaluer le modèle, comme dans l’exemple suivant :

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```
