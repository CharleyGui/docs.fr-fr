---
title: 'Exemple : Résolution des problèmes de programmation dynamique'
ms.date: 03/30/2017
ms.assetid: 42ed860a-a022-4682-8b7f-7c9870784671
ms.openlocfilehash: 0cff232668b9eb65b09a22b14e4ae58673ccd6d0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288071"
---
# <a name="example-troubleshooting-dynamic-programming"></a><span data-ttu-id="9d176-102">Exemple : Résolution des problèmes de programmation dynamique</span><span class="sxs-lookup"><span data-stu-id="9d176-102">Example: Troubleshooting Dynamic Programming</span></span>

> [!NOTE]
> <span data-ttu-id="9d176-103">Cette rubrique fait référence à .NET Native Developer Preview, qui correspond à la version préliminaire du logiciel.</span><span class="sxs-lookup"><span data-stu-id="9d176-103">This topic refers to the .NET Native Developer Preview, which is pre-release software.</span></span> <span data-ttu-id="9d176-104">Vous pouvez télécharger la préversion sur le [site web Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (inscription nécessaire).</span><span class="sxs-lookup"><span data-stu-id="9d176-104">You can download the preview from the [Microsoft Connect website](https://go.microsoft.com/fwlink/?LinkId=394611) (requires registration).</span></span>  
  
 <span data-ttu-id="9d176-105">Les échecs de recherche de métadonnées dans les applications développées à l’aide de la chaîne d’outils .NET Native entraînent une exception.</span><span class="sxs-lookup"><span data-stu-id="9d176-105">Not all metadata lookup failures in apps developed using the .NET Native tool chain result in an exception.</span></span>  <span data-ttu-id="9d176-106">Certains peuvent se manifester de manière imprévisible dans une application.</span><span class="sxs-lookup"><span data-stu-id="9d176-106">Some can manifest in unpredictable ways in an app.</span></span>  <span data-ttu-id="9d176-107">L'exemple suivant montre une violation d'accès provoquée par le référencement d'un objet null :</span><span class="sxs-lookup"><span data-stu-id="9d176-107">The following example shows an access violation caused by referencing a null object:</span></span>  
  
```output
Access violation - code c0000005 (first chance)  
App!$3_App::Core::Util::NavigationArgs.Setup  
App!$3_App::Core::Util::NavigationArgs..ctor  
App!$0_App::Gibbon::Util::DesktopNavigationArgs..ctor  
App!$0_App::ViewModels::DesktopAppVM.NavigateToPage  
App!$3_App::Core::ViewModels::AppViewModel.NavigateToFirstPage  
App!$3_App::Core::ViewModels::AppViewModel::<HandleLaunch>d__a.MoveNext  
App!$43_System::Runtime::CompilerServices::AsyncMethodBuilderCore.CallMoveNext  
App!System::Action.InvokeClosedStaticThunk  
App!System::Action.Invoke  
App!$43_System::Threading::Tasks::AwaitTaskContinuation.InvokeAction  
App!$43_System::Threading::SendOrPostCallback.InvokeOpenStaticThunk  
[snip]  
```  
  
 <span data-ttu-id="9d176-108">Nous allons essayer de résoudre les problèmes liés à cette exception à l’aide de l’approche en trois étapes décrite dans la section « Résoudre manuellement les métadonnées manquantes » de [Prise en main](getting-started-with-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="9d176-108">Let's try to troubleshoot this exception by using the three-step approach outlined in the "Manually resolve missing metadata" section of [Getting Started](getting-started-with-net-native.md).</span></span>  
  
## <a name="what-was-the-app-doing"></a><span data-ttu-id="9d176-109">Que faisait l’application ?</span><span class="sxs-lookup"><span data-stu-id="9d176-109">What was the app doing?</span></span>  

 <span data-ttu-id="9d176-110">La première chose à noter est le mécanisme de mot clé `async` à la base de la pile.</span><span class="sxs-lookup"><span data-stu-id="9d176-110">The first thing to note is the `async` keyword machinery at the base of the stack.</span></span>  <span data-ttu-id="9d176-111">Déterminer ce que l'application était effectivement en train de faire dans une méthode `async` peut être problématique, car la pile a perdu le contexte de l'appel d'origine et a exécuté le code `async` sur un thread différent.</span><span class="sxs-lookup"><span data-stu-id="9d176-111">Determining what the app was really doing in an `async` method can be problematic, because the stack has lost the context of the originating call and has run the `async` code on a different thread.</span></span> <span data-ttu-id="9d176-112">Toutefois, nous pouvons déduire que l'application essaie de charger sa première page.</span><span class="sxs-lookup"><span data-stu-id="9d176-112">However, we can deduce that the app is trying to load its first page.</span></span>  <span data-ttu-id="9d176-113">Dans l'implémentation de `NavigationArgs.Setup`, le code suivant a provoqué la violation d'accès :</span><span class="sxs-lookup"><span data-stu-id="9d176-113">In the implementation for `NavigationArgs.Setup`, the following code caused the access violation:</span></span>  
  
`AppViewModel.Current.LayoutVM.PageMap`  
  
 <span data-ttu-id="9d176-114">Dans ce cas, la propriété `LayoutVM` sur `AppViewModel.Current` avait pour valeur **null**.</span><span class="sxs-lookup"><span data-stu-id="9d176-114">In this instance, the `LayoutVM` property on `AppViewModel.Current` was **null**.</span></span>  <span data-ttu-id="9d176-115">Une absence de métadonnées a provoqué une différence de comportement subtile et a abouti à la non-initialisation d'une propriété, alors qu'elle devait être définie du point de vue de l'application.</span><span class="sxs-lookup"><span data-stu-id="9d176-115">Some absence of metadata caused a subtle behavior difference and resulted in a property being uninitialized instead of set, as the app expected.</span></span>  <span data-ttu-id="9d176-116">Définir un point d'arrêt dans le code là où `LayoutVM` aurait dû être initialisée peut nous éclairer sur la situation.</span><span class="sxs-lookup"><span data-stu-id="9d176-116">Setting a breakpoint in the code where `LayoutVM` should have been initialized might throw light on the situation.</span></span>  <span data-ttu-id="9d176-117">Toutefois, notez que le type de `LayoutVM` est `App.Core.ViewModels.Layout.LayoutApplicationVM`.</span><span class="sxs-lookup"><span data-stu-id="9d176-117">However, note that `LayoutVM`’s type is `App.Core.ViewModels.Layout.LayoutApplicationVM`.</span></span>  <span data-ttu-id="9d176-118">La seule directive de métadonnées présente jusqu'à présent dans le fichier rd.xml est la suivante :</span><span class="sxs-lookup"><span data-stu-id="9d176-118">The only metadata directive present so far in the rd.xml file is:</span></span>  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 <span data-ttu-id="9d176-119">L'échec est peut-être dû à l'absence de métadonnées dans `App.Core.ViewModels.Layout.LayoutApplicationVM`, car elles se trouvent dans un espace de noms différent.</span><span class="sxs-lookup"><span data-stu-id="9d176-119">A likely candidate for the failure is that `App.Core.ViewModels.Layout.LayoutApplicationVM` is missing metadata because it's in a different namespace.</span></span>  
  
 <span data-ttu-id="9d176-120">Dans ce cas, l'ajout d'une directive runtime pour `App.Core.ViewModels` a résolu le problème.</span><span class="sxs-lookup"><span data-stu-id="9d176-120">In this case, adding a runtime directive for `App.Core.ViewModels` resolved the issue.</span></span> <span data-ttu-id="9d176-121">Le problème était dû à un appel d’API en direction de la méthode <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> ayant retourné **null**, et l’application a ignoré silencieusement le problème jusqu’à ce qu’un incident se produise.</span><span class="sxs-lookup"><span data-stu-id="9d176-121">The root cause was an API call to the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method that returned **null**, and the app silently ignored the problem until a crash occurred.</span></span>  
  
 <span data-ttu-id="9d176-122">En programmation dynamique, il est recommandé d’utiliser les <xref:System.Type.GetType%2A?displayProperty=nameWithType> surcharges qui lèvent une exception en cas d’échec lors de l’utilisation des API de réflexion sous .net native.</span><span class="sxs-lookup"><span data-stu-id="9d176-122">In dynamic programming, a good practice when using reflection APIs under .NET Native is to use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> overloads that throw an exception on failure.</span></span>  
  
## <a name="is-this-an-isolated-case"></a><span data-ttu-id="9d176-123">S'agit-il d'un cas isolé ?</span><span class="sxs-lookup"><span data-stu-id="9d176-123">Is this an isolated case?</span></span>  

 <span data-ttu-id="9d176-124">D'autres problèmes peuvent également survenir pendant l'utilisation d'`App.Core.ViewModels`.</span><span class="sxs-lookup"><span data-stu-id="9d176-124">Other issues might also arise when using `App.Core.ViewModels`.</span></span>  <span data-ttu-id="9d176-125">Vous devez décider s'il est nécessaire d'identifier et de corriger chaque exception de métadonnées manquantes, ou d'économiser du temps et d'ajouter des directives pour une classe de types plus grande.</span><span class="sxs-lookup"><span data-stu-id="9d176-125">You must decide whether it’s worth identifying and fixing each missing metadata exception, or saving time and adding directives for a larger class of types.</span></span>  <span data-ttu-id="9d176-126">En l'occurrence, ajouter des métadonnées `dynamic` pour `App.Core.ViewModels` peut être la meilleure méthode si l'augmentation résultante de la taille du fichier binaire de sortie n'est pas un problème.</span><span class="sxs-lookup"><span data-stu-id="9d176-126">Here, adding `dynamic` metadata for `App.Core.ViewModels` might be the best approach if the resulting size increase of the output binary isn’t an issue.</span></span>  
  
## <a name="could-the-code-be-rewritten"></a><span data-ttu-id="9d176-127">Le code peut-il être réécrit ?</span><span class="sxs-lookup"><span data-stu-id="9d176-127">Could the code be rewritten?</span></span>  

 <span data-ttu-id="9d176-128">Si l'application a utilisé `typeof(LayoutApplicationVM)` à la place de `Type.GetType("LayoutApplicationVM")`, la chaîne d'outils peut avoir conservé des métadonnées `browse`.</span><span class="sxs-lookup"><span data-stu-id="9d176-128">If the app had used `typeof(LayoutApplicationVM)` instead of `Type.GetType("LayoutApplicationVM")`, the tool chain could have preserved `browse` metadata.</span></span>  <span data-ttu-id="9d176-129">Toutefois, elle n’aurait pas créé de métadonnées `invoke`, ce qui aurait abouti à une exception [MissingMetadataException](missingmetadataexception-class-net-native.md) à l’occasion de l’instanciation du type.</span><span class="sxs-lookup"><span data-stu-id="9d176-129">However, it still wouldn't have created `invoke` metadata, which would have led to a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception when instantiating the type.</span></span> <span data-ttu-id="9d176-130">Pour empêcher cette exception, vous devriez quand même ajouter une directive runtime pour l'espace de noms ou le type qui spécifie la stratégie `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="9d176-130">To prevent the exception, you'd still have to add a runtime directive for the namespace or the type that specifies the `dynamic` policy.</span></span> <span data-ttu-id="9d176-131">Pour plus d’informations sur les directives runtime, consultez le [Guide de référence du fichier de configuration des directives runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="9d176-131">For information on runtime directives, see the [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d176-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d176-132">See also</span></span>

- [<span data-ttu-id="9d176-133">Prise en main</span><span class="sxs-lookup"><span data-stu-id="9d176-133">Getting Started</span></span>](getting-started-with-net-native.md)
- [<span data-ttu-id="9d176-134">Exemple : Gestion des exceptions pendant la liaison de données</span><span class="sxs-lookup"><span data-stu-id="9d176-134">Example: Handling Exceptions When Binding Data</span></span>](example-handling-exceptions-when-binding-data.md)
