---
ms.openlocfilehash: eb89cbc72d8b09fd1aa5bc775a6c539eb208fa70
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614575"
---
### <a name="wpf-pointer-based-touch-stack"></a><span data-ttu-id="6930d-101">Pile tactile basée sur un pointeur WPF</span><span class="sxs-lookup"><span data-stu-id="6930d-101">WPF Pointer-Based Touch Stack</span></span>

#### <a name="details"></a><span data-ttu-id="6930d-102">Détails</span><span class="sxs-lookup"><span data-stu-id="6930d-102">Details</span></span>

<span data-ttu-id="6930d-103">Ce changement ajoute la possibilité d’activer une pile facultative tactile/de stylet WPF basée sur WM_POINTER.</span><span class="sxs-lookup"><span data-stu-id="6930d-103">This change adds the ability to enable an optional WM_POINTER based WPF touch/stylus stack.</span></span>  <span data-ttu-id="6930d-104">Les développeurs qui n’activent pas ceci explicitement ne devraient voir aucun changement de comportement tactile/du stylet dans WPF. Problèmes connus actuels avec la pile facultative tactile/de stylet basée sur WM_POINTER :</span><span class="sxs-lookup"><span data-stu-id="6930d-104">Developers that do not explicitly enable this should see no change in WPF touch/stylus behavior.Current Known Issues With optional WM_POINTER based touch/stylus stack:</span></span>

- <span data-ttu-id="6930d-105">Pas de prise en charge de l’écriture manuscrite en temps réel.</span><span class="sxs-lookup"><span data-stu-id="6930d-105">No support for real-time inking.</span></span>
- <span data-ttu-id="6930d-106">Bien que les plug-ins pour l’écriture manuscrite et le stylet fonctionnent toujours, ils sont traités sur le thread d’interface utilisateur, ce qui peut entraîner une baisse des performances.</span><span class="sxs-lookup"><span data-stu-id="6930d-106">While inking and StylusPlugins will still work, they will be processed on the UI Thread which can lead to poor performance.</span></span>
- <span data-ttu-id="6930d-107">Changements de comportement en raison de changements dans la promotion d’événements tactiles/de stylet en événements de souris</span><span class="sxs-lookup"><span data-stu-id="6930d-107">Behavioral changes due to changes in promotion from touch/stylus events to mouse events</span></span>
- <span data-ttu-id="6930d-108">La manipulation peut se comporter différemment</span><span class="sxs-lookup"><span data-stu-id="6930d-108">Manipulation may behave differently</span></span>
- <span data-ttu-id="6930d-109">Le glisser-déplacer ne réagit pas correctement à l’entrée tactile</span><span class="sxs-lookup"><span data-stu-id="6930d-109">Drag/Drop will not show appropriate feedback for touch input</span></span>
- <span data-ttu-id="6930d-110">Cela n’affecte pas l’entrée du stylet</span><span class="sxs-lookup"><span data-stu-id="6930d-110">This does not affect stylus input</span></span>
- <span data-ttu-id="6930d-111">Le glisser-déplacer ne peut plus être lancé par des événements tactiles/du stylet</span><span class="sxs-lookup"><span data-stu-id="6930d-111">Drag/Drop can no longer be initiated on touch/stylus events</span></span>
- <span data-ttu-id="6930d-112">Cela peut éventuellement bloquer l’application jusqu'à ce que l’entrée de la souris soit détectée.</span><span class="sxs-lookup"><span data-stu-id="6930d-112">This can potentially hang the application until mouse input is detected.</span></span>
- <span data-ttu-id="6930d-113">Au lieu de cela, les développeurs doivent lancer le glisser-déplacer à partir des événements de souris.</span><span class="sxs-lookup"><span data-stu-id="6930d-113">Instead, developers should initiate drag and drop from mouse events.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6930d-114">Suggestion</span><span class="sxs-lookup"><span data-stu-id="6930d-114">Suggestion</span></span>

<span data-ttu-id="6930d-115">Les développeurs qui souhaitent activer cette pile peuvent ajouter/fusionner les éléments suivants dans le fichier App.config de l’application :</span><span class="sxs-lookup"><span data-stu-id="6930d-115">Developers who wish to enable this stack can add/merge the following to their application's App.config file:</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Input.Stylus.EnablePointerSupport=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

<span data-ttu-id="6930d-116">La suppression de cette entrée ou l’affectation de la valeur false désactive cette pile facultative. Notez que cette pile est uniquement disponible sur Windows 10 Creators Update et ultérieur.</span><span class="sxs-lookup"><span data-stu-id="6930d-116">Removing this or setting the value to false will turn this optional stack off.Note that this stack is available only on Windows 10 Creators Update and above.</span></span>

| <span data-ttu-id="6930d-117">Nom</span><span class="sxs-lookup"><span data-stu-id="6930d-117">Name</span></span>    | <span data-ttu-id="6930d-118">Valeur</span><span class="sxs-lookup"><span data-stu-id="6930d-118">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6930d-119">Étendue</span><span class="sxs-lookup"><span data-stu-id="6930d-119">Scope</span></span>   | <span data-ttu-id="6930d-120">Edge</span><span class="sxs-lookup"><span data-stu-id="6930d-120">Edge</span></span>        |
| <span data-ttu-id="6930d-121">Version</span><span class="sxs-lookup"><span data-stu-id="6930d-121">Version</span></span> | <span data-ttu-id="6930d-122">4,7</span><span class="sxs-lookup"><span data-stu-id="6930d-122">4.7</span></span>         |
| <span data-ttu-id="6930d-123">Type</span><span class="sxs-lookup"><span data-stu-id="6930d-123">Type</span></span>    | <span data-ttu-id="6930d-124">Reciblage</span><span class="sxs-lookup"><span data-stu-id="6930d-124">Retargeting</span></span> |
