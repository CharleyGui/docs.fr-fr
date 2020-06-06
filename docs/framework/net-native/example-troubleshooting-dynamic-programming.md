---
title: 'Exemple : Résolution des problèmes de programmation dynamique'
ms.date: 03/30/2017
ms.assetid: 42ed860a-a022-4682-8b7f-7c9870784671
ms.openlocfilehash: ff179854066d024a89cb5a84a19d0b9bb054d6e5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128440"
---
# <a name="example-troubleshooting-dynamic-programming"></a>Exemple : Résolution des problèmes de programmation dynamique
> [!NOTE]
> Cette rubrique fait référence à .NET Native Developer Preview, qui correspond à la version préliminaire du logiciel. Vous pouvez télécharger la préversion sur le [site web Microsoft Connect](https://go.microsoft.com/fwlink/?LinkId=394611) (inscription nécessaire).  
  
 Les échecs de recherche de métadonnées dans les applications développées à l’aide de la chaîne d’outils .NET Native entraînent une exception.  Certains peuvent se manifester de manière imprévisible dans une application.  L'exemple suivant montre une violation d'accès provoquée par le référencement d'un objet null :  
  
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
  
 Nous allons essayer de résoudre les problèmes liés à cette exception à l’aide de l’approche en trois étapes décrite dans la section « Résoudre manuellement les métadonnées manquantes » de [Prise en main](getting-started-with-net-native.md).  
  
## <a name="what-was-the-app-doing"></a>Que faisait l'application ?  
 La première chose à noter est le mécanisme de mot clé `async` à la base de la pile.  Déterminer ce que l'application était effectivement en train de faire dans une méthode `async` peut être problématique, car la pile a perdu le contexte de l'appel d'origine et a exécuté le code `async` sur un thread différent. Toutefois, nous pouvons déduire que l'application essaie de charger sa première page.  Dans l'implémentation de `NavigationArgs.Setup`, le code suivant a provoqué la violation d'accès :  
  
`AppViewModel.Current.LayoutVM.PageMap`  
  
 Dans ce cas, la propriété `LayoutVM` sur `AppViewModel.Current` avait pour valeur **null**.  Une absence de métadonnées a provoqué une différence de comportement subtile et a abouti à la non-initialisation d'une propriété, alors qu'elle devait être définie du point de vue de l'application.  Définir un point d'arrêt dans le code là où `LayoutVM` aurait dû être initialisée peut nous éclairer sur la situation.  Toutefois, notez que le type de `LayoutVM` est `App.Core.ViewModels.Layout.LayoutApplicationVM`.  La seule directive de métadonnées présente jusqu'à présent dans le fichier rd.xml est la suivante :  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 L'échec est peut-être dû à l'absence de métadonnées dans `App.Core.ViewModels.Layout.LayoutApplicationVM`, car elles se trouvent dans un espace de noms différent.  
  
 Dans ce cas, l'ajout d'une directive runtime pour `App.Core.ViewModels` a résolu le problème. Le problème était dû à un appel d’API en direction de la méthode <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> ayant retourné **null**, et l’application a ignoré silencieusement le problème jusqu’à ce qu’un incident se produise.  
  
 En programmation dynamique, il est recommandé d’utiliser les <xref:System.Type.GetType%2A?displayProperty=nameWithType> surcharges qui lèvent une exception en cas d’échec lors de l’utilisation des API de réflexion sous .net native.  
  
## <a name="is-this-an-isolated-case"></a>S'agit-il d'un cas isolé ?  
 D'autres problèmes peuvent également survenir pendant l'utilisation d'`App.Core.ViewModels`.  Vous devez décider s'il est nécessaire d'identifier et de corriger chaque exception de métadonnées manquantes, ou d'économiser du temps et d'ajouter des directives pour une classe de types plus grande.  En l'occurrence, ajouter des métadonnées `dynamic` pour `App.Core.ViewModels` peut être la meilleure méthode si l'augmentation résultante de la taille du fichier binaire de sortie n'est pas un problème.  
  
## <a name="could-the-code-be-rewritten"></a>Le code peut-il être réécrit ?  
 Si l'application a utilisé `typeof(LayoutApplicationVM)` à la place de `Type.GetType("LayoutApplicationVM")`, la chaîne d'outils peut avoir conservé des métadonnées `browse`.  Toutefois, elle n’aurait pas créé de métadonnées `invoke`, ce qui aurait abouti à une exception [MissingMetadataException](missingmetadataexception-class-net-native.md) à l’occasion de l’instanciation du type. Pour empêcher cette exception, vous devriez quand même ajouter une directive runtime pour l'espace de noms ou le type qui spécifie la stratégie `dynamic`. Pour plus d’informations sur les directives runtime, consultez le [Guide de référence du fichier de configuration des directives runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md).  
  
## <a name="see-also"></a>Voir aussi

- [Prise en main](getting-started-with-net-native.md)
- [Exemple : Gestion des exceptions pendant la liaison de données](example-handling-exceptions-when-binding-data.md)
