---
title: Règles de documentation (analyse du code)
description: En savoir plus sur les règles de documentation des règles d’analyse du code
ms.date: 09/16/2019
ms.topic: reference
f1_keywords:
- vs.codeanalysis.documentationrules
helpviewer_keywords:
- documentation rules
- managed code analysis rules, documentation rules
- warnings, documentation
author: mavasani
ms.author: mavasani
ms.openlocfilehash: 29d1734eec29bd00d456b4b00c48c2e8ef223441
ms.sourcegitcommit: 2e4adc490c1d2a705a0592b295d606b10b9f51f1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2020
ms.locfileid: "96587218"
---
# <a name="documentation-rules"></a>Règles de documentation

Les règles de documentation prennent en charge l’écriture de bibliothèques bien documentées via l’utilisation correcte des [Commentaires de documentation XML](../../../csharp/codedoc.md) pour les API visibles de l’extérieur.

## <a name="in-this-section"></a>Dans cette section

| Règle | Description |
| - | - |
| [CA1200 : Éviter d’utiliser des balises cref avec un préfixe](ca1200.md) | L’attribut [cref](../../../csharp/programming-guide/xmldoc/cref-attribute.md) dans une balise de documentation XML signifie « référence du code ». Il indique que le texte interne de la balise est un élément de code tel qu’un type, une méthode ou une propriété. Évitez `cref` d’utiliser des balises avec des préfixes, car cela empêche le compilateur de vérifier les références. Cela empêche également l’environnement de développement intégré (IDE) de Visual Studio de rechercher et de mettre à jour ces références de symboles lors des refactorisations. |
