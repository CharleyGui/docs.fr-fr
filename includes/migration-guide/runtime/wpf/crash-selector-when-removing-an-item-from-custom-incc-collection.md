---
ms.openlocfilehash: f50022d9a7bacd7be40fe3050ced26e7c25cf7aa
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496149"
---
### <a name="crash-in-selector-when-removing-an-item-from-a-custom-incc-collection"></a><span data-ttu-id="ee0e3-101">Plantage dans le sélecteur lors de la suppression d’un élément d’une collection INCC personnalisée</span><span class="sxs-lookup"><span data-stu-id="ee0e3-101">Crash in Selector when removing an item from a custom INCC collection</span></span>

#### <a name="details"></a><span data-ttu-id="ee0e3-102">Détails</span><span class="sxs-lookup"><span data-stu-id="ee0e3-102">Details</span></span>

<span data-ttu-id="ee0e3-103">Une <code>T:System.InvalidOperationException</code> peut se produire dans les scénarios suivants :</span><span class="sxs-lookup"><span data-stu-id="ee0e3-103">An <code>T:System.InvalidOperationException</code> can occur in the following scenario:</span></span><ul><li><span data-ttu-id="ee0e3-104">L’ItemsSource pour une collection <code>T:System.Windows.Controls.Primitives.Selector</code> est une collection avec une implémentation personnalisée de <code>T:System.Collections.Specialized.INotifyCollectionChanged</code>.</span><span class="sxs-lookup"><span data-stu-id="ee0e3-104">The ItemsSource for a <code>T:System.Windows.Controls.Primitives.Selector</code> is a collection with a custom implementation of <code>T:System.Collections.Specialized.INotifyCollectionChanged</code>.</span></span></li><li><span data-ttu-id="ee0e3-105">L’élément sélectionné est supprimé de la collection.</span><span class="sxs-lookup"><span data-stu-id="ee0e3-105">The selected item is removed from the collection.</span></span></li><li><span data-ttu-id="ee0e3-106">Le <code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> a <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> = -1 (indiquant une position inconnue).</span><span class="sxs-lookup"><span data-stu-id="ee0e3-106">The <code>T:System.Collections.Specialized.NotifyCollectionChangedEventArgs</code> has <code>P:System.Collections.Specialized.NotifyCollectionChangedEventArgs.OldStartingIndex</code> = -1 (indicating an unknown position).</span></span></li></ul><span data-ttu-id="ee0e3-107">La pile des appels de l’exception commence à System.Windows.Threading.Dispatcher.VerifyAccess() à System.Windows.DependencyObject.GetValue(DependencyProperty dp) à System.Windows.Controls.Primitives.Selector.GetIsSelected(DependencyObject element). Cette exception peut se produire dans .NET Framework 4.5 si l’application a plusieurs threads de répartiteur.</span><span class="sxs-lookup"><span data-stu-id="ee0e3-107">The exception's callstack begins at System.Windows.Threading.Dispatcher.VerifyAccess() at System.Windows.DependencyObject.GetValue(DependencyProperty dp) at System.Windows.Controls.Primitives.Selector.GetIsSelected(DependencyObject element)This exception can occur in .NET Framework 4.5 if the application has more than one Dispatcher thread.</span></span> <span data-ttu-id="ee0e3-108">Dans .NET Framework 4.7, l’exception peut également se produire dans les applications avec un seul thread de répartiteur.</span><span class="sxs-lookup"><span data-stu-id="ee0e3-108">In .NET Framework 4.7 the exception can also occur in applications with a single Dispatcher thread.</span></span> <span data-ttu-id="ee0e3-109">Le problème est résolu dans .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="ee0e3-109">The issue is fixed in .NET Framework 4.7.1.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ee0e3-110">Suggestion</span><span class="sxs-lookup"><span data-stu-id="ee0e3-110">Suggestion</span></span>

<span data-ttu-id="ee0e3-111">Mettre à niveau vers .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="ee0e3-111">Upgrade to .NET Framework 4.7.1.</span></span>

| <span data-ttu-id="ee0e3-112">Name</span><span class="sxs-lookup"><span data-stu-id="ee0e3-112">Name</span></span>    | <span data-ttu-id="ee0e3-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="ee0e3-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ee0e3-114">Étendue</span><span class="sxs-lookup"><span data-stu-id="ee0e3-114">Scope</span></span>   |<span data-ttu-id="ee0e3-115">Secondaire</span><span class="sxs-lookup"><span data-stu-id="ee0e3-115">Minor</span></span>|
|<span data-ttu-id="ee0e3-116">Version</span><span class="sxs-lookup"><span data-stu-id="ee0e3-116">Version</span></span>|<span data-ttu-id="ee0e3-117">4,7</span><span class="sxs-lookup"><span data-stu-id="ee0e3-117">4.7</span></span>|
|<span data-ttu-id="ee0e3-118">Type</span><span class="sxs-lookup"><span data-stu-id="ee0e3-118">Type</span></span>|<span data-ttu-id="ee0e3-119">Runtime</span><span class="sxs-lookup"><span data-stu-id="ee0e3-119">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="ee0e3-120">API affectées</span><span class="sxs-lookup"><span data-stu-id="ee0e3-120">Affected APIs</span></span>

<span data-ttu-id="ee0e3-121">Non détectable via l’analyse des API.</span><span class="sxs-lookup"><span data-stu-id="ee0e3-121">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
