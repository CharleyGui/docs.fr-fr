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
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality"></a><span data-ttu-id="a7f37-103">Calculer des métriques pour évaluer la qualité du modèle Machine Learning</span><span class="sxs-lookup"><span data-stu-id="a7f37-103">Calculate metrics to evaluate machine learning model quality</span></span>

> [!NOTE]
> <span data-ttu-id="a7f37-104">Cette rubrique fait référence à ML.NET, actuellement en préversion, et les ressources sont susceptibles d’être modifiées.</span><span class="sxs-lookup"><span data-stu-id="a7f37-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="a7f37-105">Pour plus d’informations, visitez la page [ML.NET.](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet)</span><span class="sxs-lookup"><span data-stu-id="a7f37-105">For more information, visit the [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) page.</span></span>

<span data-ttu-id="a7f37-106">Ce guide pratique et l’exemple associé utilisent actuellement **ML.NET version 0.10**.</span><span class="sxs-lookup"><span data-stu-id="a7f37-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="a7f37-107">Pour plus d’informations, voir les notes de publication dans le référentiel GitHub [dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="a7f37-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="a7f37-108">Comment évaluer la qualité après avoir entraîné le modèle ?</span><span class="sxs-lookup"><span data-stu-id="a7f37-108">How do you evaluate quality after you train the model?</span></span> <span data-ttu-id="a7f37-109">Chaque tâche de machine learning expose des métriques pour l’évaluation de la qualité.</span><span class="sxs-lookup"><span data-stu-id="a7f37-109">Each machine learning task exposes metrics for quality evaluation.</span></span>

<span data-ttu-id="a7f37-110">Vous pouvez utiliser le « contexte » correspondant de la tâche pour évaluer le modèle, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="a7f37-110">You can use the corresponding 'context' of the task to evaluate the model, as in the following example:</span></span>

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```
