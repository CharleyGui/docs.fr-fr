---
ms.openlocfilehash: 97ca78e154eb25e863256e06caa119fe753bc344
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858417"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a><span data-ttu-id="b1849-101">La correction orthographique WPF dans les contrôles acceptant du texte ne fonctionne pas dans Windows 10 pour les langues qui ne figurent pas dans la liste des langues d’entrée du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="b1849-101">WPF spell checking in text-enabled controls will not work in Windows 10 for languages not in the OS's input language list</span></span>

|   |   |
|---|---|
|<span data-ttu-id="b1849-102">Détails</span><span class="sxs-lookup"><span data-stu-id="b1849-102">Details</span></span>|<span data-ttu-id="b1849-103">Lors de l’exécution sur Windows 10, le vérificateur orthographique peut ne pas fonctionner pour les contrôles WPF acceptant du texte, car les fonctionnalités de vérification orthographique de la plateforme sont disponibles seulement pour les langues présentes dans la liste des langues d’entrée. Dans Windows 10, quand une langue est ajoutée à la liste des claviers disponibles, Windows télécharge et installe automatiquement un package correspondant de fonctionnalités à la demande qui fournit les fonctionnalités de vérification orthographique.</span><span class="sxs-lookup"><span data-stu-id="b1849-103">When running on Windows 10, the spell checker may not work for WPF text-enabled controls because platform spell-checking capabilities are available only for languages present in the input languages list.In Windows 10, when a language is added to the list of available keyboards, Windows automatically downloads and installs a corresponding Feature on Demand (FOD) package that provides spell-checking capabilities.</span></span> <span data-ttu-id="b1849-104">En ajoutant la langue à la liste des langues d'entrée, le vérificateur d'orthographe est pris en charge.</span><span class="sxs-lookup"><span data-stu-id="b1849-104">By adding the language to the input languages list, the spell checker will be supported.</span></span>|
|<span data-ttu-id="b1849-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="b1849-105">Suggestion</span></span>|<span data-ttu-id="b1849-106">Pour que cela fonctionne dans Windows 10, n’oubliez pas que la langue ou le texte à vérifier doit être ajouté comme langue d’entrée pour la vérification orthographique.</span><span class="sxs-lookup"><span data-stu-id="b1849-106">Be aware that the language or text to be spell-checked must be added as an input language for spell-checking to work in Windows 10.</span></span>|
|<span data-ttu-id="b1849-107">Portée</span><span class="sxs-lookup"><span data-stu-id="b1849-107">Scope</span></span>|<span data-ttu-id="b1849-108">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="b1849-108">Edge</span></span>|
|<span data-ttu-id="b1849-109">Version</span><span class="sxs-lookup"><span data-stu-id="b1849-109">Version</span></span>|<span data-ttu-id="b1849-110">4.6</span><span class="sxs-lookup"><span data-stu-id="b1849-110">4.6</span></span>|
|<span data-ttu-id="b1849-111">Type</span><span class="sxs-lookup"><span data-stu-id="b1849-111">Type</span></span>|<span data-ttu-id="b1849-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="b1849-112">Runtime</span></span>|

