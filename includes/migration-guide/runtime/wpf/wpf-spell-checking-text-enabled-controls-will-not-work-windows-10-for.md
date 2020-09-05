---
ms.openlocfilehash: 6d7f998cda6326e1f584713576a0aa27b3a68655
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497485"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a><span data-ttu-id="60782-101">La correction orthographique WPF dans les contrôles acceptant du texte ne fonctionne pas dans Windows 10 pour les langues qui ne figurent pas dans la liste des langues d’entrée du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="60782-101">WPF spell checking in text-enabled controls will not work in Windows 10 for languages not in the OS's input language list</span></span>

#### <a name="details"></a><span data-ttu-id="60782-102">Détails</span><span class="sxs-lookup"><span data-stu-id="60782-102">Details</span></span>

<span data-ttu-id="60782-103">Lors de l’exécution sur Windows 10, le vérificateur orthographique peut ne pas fonctionner pour les contrôles WPF acceptant du texte, car les fonctionnalités de vérification orthographique de la plateforme sont disponibles seulement pour les langues présentes dans la liste des langues d’entrée. Dans Windows 10, quand une langue est ajoutée à la liste des claviers disponibles, Windows télécharge et installe automatiquement un package correspondant de fonctionnalités à la demande qui fournit les fonctionnalités de vérification orthographique.</span><span class="sxs-lookup"><span data-stu-id="60782-103">When running on Windows 10, the spell checker may not work for WPF text-enabled controls because platform spell-checking capabilities are available only for languages present in the input languages list.In Windows 10, when a language is added to the list of available keyboards, Windows automatically downloads and installs a corresponding Feature on Demand (FOD) package that provides spell-checking capabilities.</span></span> <span data-ttu-id="60782-104">En ajoutant la langue à la liste des langues d'entrée, le vérificateur d'orthographe est pris en charge.</span><span class="sxs-lookup"><span data-stu-id="60782-104">By adding the language to the input languages list, the spell checker will be supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="60782-105">Suggestion</span><span class="sxs-lookup"><span data-stu-id="60782-105">Suggestion</span></span>

<span data-ttu-id="60782-106">Pour que cela fonctionne dans Windows 10, n’oubliez pas que la langue ou le texte à vérifier doit être ajouté comme langue d’entrée pour la vérification orthographique.</span><span class="sxs-lookup"><span data-stu-id="60782-106">Be aware that the language or text to be spell-checked must be added as an input language for spell-checking to work in Windows 10.</span></span>

| <span data-ttu-id="60782-107">Name</span><span class="sxs-lookup"><span data-stu-id="60782-107">Name</span></span>    | <span data-ttu-id="60782-108">Valeur</span><span class="sxs-lookup"><span data-stu-id="60782-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="60782-109">Étendue</span><span class="sxs-lookup"><span data-stu-id="60782-109">Scope</span></span>   |<span data-ttu-id="60782-110">Edge</span><span class="sxs-lookup"><span data-stu-id="60782-110">Edge</span></span>|
|<span data-ttu-id="60782-111">Version</span><span class="sxs-lookup"><span data-stu-id="60782-111">Version</span></span>|<span data-ttu-id="60782-112">4,6</span><span class="sxs-lookup"><span data-stu-id="60782-112">4.6</span></span>|
|<span data-ttu-id="60782-113">Type</span><span class="sxs-lookup"><span data-stu-id="60782-113">Type</span></span>|<span data-ttu-id="60782-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="60782-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="60782-115">API affectées</span><span class="sxs-lookup"><span data-stu-id="60782-115">Affected APIs</span></span>

<span data-ttu-id="60782-116">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="60782-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
