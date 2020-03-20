---
ms.openlocfilehash: abb89099c4c8a5d9c0e55ef8f357faf44e75b045
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858417"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a>La correction orthographique WPF dans les contrôles acceptant du texte ne fonctionne pas dans Windows 10 pour les langues qui ne figurent pas dans la liste des langues d’entrée du système d’exploitation

|   |   |
|---|---|
|Détails|Lors de l’exécution sur Windows 10, le vérificateur orthographique peut ne pas fonctionner pour les contrôles WPF acceptant du texte, car les fonctionnalités de vérification orthographique de la plateforme sont disponibles seulement pour les langues présentes dans la liste des langues d’entrée. Dans Windows 10, quand une langue est ajoutée à la liste des claviers disponibles, Windows télécharge et installe automatiquement un package correspondant de fonctionnalités à la demande qui fournit les fonctionnalités de vérification orthographique. En ajoutant la langue à la liste des langues d'entrée, le vérificateur d'orthographe est pris en charge.|
|Suggestion|Pour que cela fonctionne dans Windows 10, n’oubliez pas que la langue ou le texte à vérifier doit être ajouté comme langue d’entrée pour la vérification orthographique.|
|Étendue|Edge|
|Version|4.6|
|Type|Runtime|
