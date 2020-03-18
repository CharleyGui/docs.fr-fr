---
title: Expressions lambda implicitement typées
description: Découvrez pourquoi vous ne pouvez pas utiliser une déclaration de variable implicitement typée pour déclarer une expression lambda.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: ef437ef961210290db4150a8a5cfb70e01aee958
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79145720"
---
# <a name="implicitly-typed-lambda-expressions"></a>Expressions lambda implicitement typées

Vous ne pouvez pas utiliser une déclaration de variable implicitement typée pour déclarer une expression lambda,
car cela crée un problème de logique circulaire pour le compilateur. La déclaration `var` indique au compilateur de déterminer le type de la variable à partir du type de l’expression située à droite de l’opérateur d’assignation. Une expression lambda n’a pas de type au moment de la compilation, mais elle peut être convertie en n’importe quel type d’expression ou de délégué correspondant. Quand vous assignez une expression lambda à une variable d’un type de délégué ou d’expression, vous indiquez au compilateur de convertir l’expression lambda en une expression ou un délégué qui corresponde à la signature de la variable assignée. Le compilateur doit tenter de faire correspondre ce qui se trouve à droite de l’assignation avec ce qui se trouve à sa gauche.

Les deux côtés de l’assignation ne peuvent pas indiquer au compilateur d’examiner l’objet situé de l’autre côté de l’opérateur d’assignation et de vérifier si le type correspond.

Vous pouvez obtenir encore plus de détails sur les raisons pour lesquelles la langue C spécifie ce comportement en lisant [cet article](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) (téléchargement PDF).
