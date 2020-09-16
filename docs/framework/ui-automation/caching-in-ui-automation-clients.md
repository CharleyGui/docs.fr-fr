---
title: Mise en cache dans les clients UI Automation
description: Obtenir des détails sur la mise en cache dans les clients UI Automation dans .NET. La mise en cache est définie comme la pré-extraction de données.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation caching in clients
- caching, UI Automation clients
ms.assetid: 94c15031-4975-43cc-bcd5-c9439ed21c9c
ms.openlocfilehash: cbf7b18d59e468be085f245cc9bb0a595bd41832
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540925"
---
# <a name="caching-in-ui-automation-clients"></a>Mise en cache dans les clients UI Automation
> [!NOTE]
> Cette documentation s'adresse aux développeurs .NET Framework qui souhaitent utiliser les classes [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] managées définies dans l'espace de noms <xref:System.Windows.Automation>. Pour obtenir les dernières informations sur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consultez [API Windows Automation : UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 Cette rubrique présente la mise en cache des modèles de contrôle et des propriétés [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .  
  
 Dans [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], la mise en cache correspond à la prérécupération des données. Les données sont ensuite accessibles sans communication interprocessus supplémentaire. La mise en cache est généralement utilisée par les applications clientes UI Automation pour récupérer des propriétés et des modèles de contrôle en bloc. Les informations sont ensuite récupérées à partir du cache selon les besoins. L’application met à jour le cache périodiquement, habituellement en réponse aux événements signifiant que quelque chose a changé dans l’ [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] .  
  
 Les avantages de la mise en cache sont plus perceptibles avec les contrôles Windows Presentation Foundation (WPF) et les contrôles personnalisés qui ont des fournisseurs UI Automation côté serveur. L’accès aux fournisseurs côté client, tels que les fournisseurs par défaut pour les contrôles Win32, présente moins d’avantages.  
  
 La mise en cache se produit lorsque l’application active un <xref:System.Windows.Automation.CacheRequest> puis utilise une méthode ou une propriété qui retourne un <xref:System.Windows.Automation.AutomationElement>. Par exemple, <xref:System.Windows.Automation.AutomationElement.FindFirst%2A>, <xref:System.Windows.Automation.AutomationElement.FindAll%2A>. Les méthodes de la classe <xref:System.Windows.Automation.TreeWalker> font exception à cette règle. La mise en cache s’effectue uniquement si un <xref:System.Windows.Automation.CacheRequest> est spécifié comme paramètre (par exemple, <xref:System.Windows.Automation.TreeWalker.GetFirstChild%28System.Windows.Automation.AutomationElement%2CSystem.Windows.Automation.CacheRequest%29?displayProperty=nameWithType>.  
  
 La mise en cache se produit également lorsque vous vous abonnez à un événement alors qu’un <xref:System.Windows.Automation.CacheRequest> est actif. L’objet <xref:System.Windows.Automation.AutomationElement> passé au gestionnaire d’événements comme source d’un événement contient les propriétés mises en cache et les modèles spécifiés par le <xref:System.Windows.Automation.CacheRequest>d’origine. Toute modification apportée au <xref:System.Windows.Automation.CacheRequest> après votre abonnement à l’événement n’a aucun effet.  
  
 Il est possible de mettre en cache les propriétés et les modèles de contrôle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] d’un élément.  
  
<a name="Options_for_Caching"></a>
## <a name="options-for-caching"></a>Options de mise en cache  
 <xref:System.Windows.Automation.CacheRequest> spécifie les options suivantes de mise en cache.  
  
<a name="Properties_to_Cache"></a>
### <a name="properties-to-cache"></a>Propriétés à mettre en cache  
 Vous pouvez spécifier des propriétés à mettre en cache en appelant <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationProperty%29> pour chaque propriété avant d’activer la requête.  
  
<a name="Control_Patterns_to_Cache"></a>
### <a name="control-patterns-to-cache"></a>Modèles de contrôle à mettre en cache  
 Vous pouvez spécifier des modèles de contrôle à mettre en cache en appelant <xref:System.Windows.Automation.CacheRequest.Add%28System.Windows.Automation.AutomationPattern%29> pour chaque modèle avant d’activer la requête. Lorsqu’un modèle est mis en cache, ses propriétés ne sont pas automatiquement mises en cache. Vous devez spécifier les propriétés que vous voulez mettre en cache en utilisant <xref:System.Windows.Automation.CacheRequest.Add%2A?displayProperty=nameWithType>.  
  
<a name="Scope_of_the_Caching"></a>
### <a name="scope-and-filtering-of-caching"></a>Portée et filtrage de la mise en cache  
 Vous pouvez spécifier les éléments dont vous voulez mettre en cache les propriétés et les modèles en définissant la propriété <xref:System.Windows.Automation.CacheRequest.TreeScope%2A?displayProperty=nameWithType> avant d’activer la requête. La portée est relative aux éléments qui sont récupérés lorsque la requête est active. Par exemple, si vous définissez uniquement <xref:System.Windows.Automation.TreeScope.Children>et que vous récupérez ensuite un <xref:System.Windows.Automation.AutomationElement>, les propriétés et les modèles des enfants de cet élément sont mis en cache, mais pas ceux de l’élément lui-même. Pour vous assurer que la mise en cache s’effectue pour l’élément récupéré lui-même, vous devez inclure <xref:System.Windows.Automation.TreeScope.Element> dans la propriété <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> . Il n’est pas possible de définir la portée sur <xref:System.Windows.Automation.TreeScope.Parent> ni <xref:System.Windows.Automation.TreeScope.Ancestors>. Toutefois, un élément parent peut être mis en cache lorsqu’un élément enfant est mis en cache. Dans cette rubrique, consultez la section Récupération des enfants et des parents mis en cache.  
  
 L’étendue de la mise en cache est également affectée par la propriété <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A?displayProperty=nameWithType> . Par défaut, la mise en cache est effectuée uniquement pour les éléments qui apparaissent dans la vue de contrôle de l’arborescence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Vous pouvez toutefois modifier cette propriété pour appliquer la mise en cache à tous les éléments ou uniquement aux éléments qui apparaissent dans la vue de contenu.  
  
<a name="Strength_of_the_Element_References"></a>
### <a name="strength-of-the-element-references"></a>Force des références d’un élément  
 Lorsque vous récupérez un <xref:System.Windows.Automation.AutomationElement>, vous avez accès par défaut à toutes les propriétés et à tous les modèles de cet élément, y compris à ceux qui n’ont pas été mis en cache. Toutefois, pour une meilleure efficacité, vous pouvez spécifier que la référence à l’élément renvoie uniquement aux données mises en cache, en affectant à la propriété <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> du <xref:System.Windows.Automation.CacheRequest> la valeur <xref:System.Windows.Automation.AutomationElementMode.None>. Dans ce cas, vous n’avez pas accès aux propriétés et aux modèles non mis en cache des éléments récupérés. Cela signifie que vous n’avez pas accès aux propriétés via <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> ou la propriété `Current` d’ <xref:System.Windows.Automation.AutomationElement> ou un modèle de contrôle quelconque. Vous ne pouvez pas non plus récupérer un modèle en utilisant <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> ou <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>. Dans les modèles mis en cache, vous pouvez appeler des méthodes qui récupèrent les propriétés de tableau, telles que <xref:System.Windows.Automation.SelectionPattern.SelectionPatternInformation.GetSelection%2A?displayProperty=nameWithType>, mais aucune qui exécute des actions sur le contrôle, comme <xref:System.Windows.Automation.InvokePattern.Invoke%2A?displayProperty=nameWithType>.  
  
 Un lecteur d’écran est un exemple d’application qui n’a pas forcément besoin de références complètes aux objets. Il prérécupère les propriétés <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> et <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> des éléments dans une fenêtre mais n’a pas besoin des objets <xref:System.Windows.Automation.AutomationElement> eux-mêmes.  
  
<a name="Activating_the_CacheRequest"></a>
## <a name="activating-the-cacherequest"></a>Activation de CacheRequest  
 La mise en cache s’effectue uniquement quand les objets <xref:System.Windows.Automation.AutomationElement> sont récupérés alors qu’un <xref:System.Windows.Automation.CacheRequest> est actif pour le thread en cours. Il existe deux façons d’activer un <xref:System.Windows.Automation.CacheRequest>.  
  
 La plus courante consiste à appeler <xref:System.Windows.Automation.CacheRequest.Activate%2A>. Cette méthode retourne un objet qui implémente <xref:System.IDisposable>. La requête reste active tant que l’objet <xref:System.IDisposable> existe. Le moyen le plus simple de contrôler la durée de vie de l’objet consiste à placer l’appel dans un `using` bloc (C#) ou `Using` (Visual Basic). Cela garantit l’extraction de la demande de la pile même si une exception est levée.  
  
 L’autre manière, utile quand vous souhaitez imbriquer des requêtes de cache, consiste à appeler <xref:System.Windows.Automation.CacheRequest.Push%2A>. Cette opération place la requête sur une pile et l’active. La requête reste active jusqu’à ce qu’elle soit supprimée de la pile par <xref:System.Windows.Automation.CacheRequest.Pop%2A>. La requête devient temporairement inactive si une autre requête est envoyée à la pile. Seule la première requête sur la pile est active.  
  
<a name="Retrieving_Cached_Properties"></a>
## <a name="retrieving-cached-properties"></a>Récupération des propriétés mises en cache  
 Vous pouvez récupérer les propriétés mises en cache d’un élément via les méthodes et les propriétés suivantes.  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.Cached%2A>  
  
 Une exception est levée si la propriété demandée ne figure pas dans le cache.  
  
 <xref:System.Windows.Automation.AutomationElement.Cached%2A>, comme <xref:System.Windows.Automation.AutomationElement.Current%2A>, expose des propriétés individuelles en tant que membres d’une structure. Toutefois, vous n’avez pas besoin de récupérer cette structure. Vous pouvez accéder directement aux propriétés individuelles. Par exemple, la propriété <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A> peut être obtenue à partir de `element.Cached.Name`, où `element` est un <xref:System.Windows.Automation.AutomationElement>.  
  
<a name="Retrieving_Cached_Control_Patterns"></a>
## <a name="retrieving-cached-control-patterns"></a>Récupération des modèles de contrôle mis en cache  
 Vous pouvez récupérer les modèles de contrôle mis en cache d’un élément via les méthodes suivantes.  
  
- <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A>  
  
- <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A>  
  
 Si le modèle n’est pas dans le cache, <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> lève une exception et <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> retourne `false`.  
  
 Vous pouvez récupérer les propriétés mises en cache d’un modèle de contrôle à l’aide de la propriété `Cached` de l’objet de modèle. Vous pouvez également récupérer les valeurs en cours via la propriété `Current` , mais uniquement si <xref:System.Windows.Automation.AutomationElementMode.None> n’a pas été spécifié quand <xref:System.Windows.Automation.AutomationElement> a été récupéré. (<xref:System.Windows.Automation.AutomationElementMode.Full> est la valeur par défaut qui donne accès aux valeurs actuelles.)  
  
<a name="Retrieving_Cached_Children_and_Parents"></a>
## <a name="retrieving-cached-children-and-parents"></a>Récupération des enfants et des parents mis en cache  
 Quand vous récupérez un <xref:System.Windows.Automation.AutomationElement> et que vous demandez la mise en cache pour les enfants de cet élément via la propriété <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> de la requête, il est possible, par la suite, d’obtenir les éléments enfants de la propriété <xref:System.Windows.Automation.AutomationElement.CachedChildren%2A> de l’élément que vous avez récupéré.  
  
 Si <xref:System.Windows.Automation.TreeScope.Element> a été inclus dans la portée de la requête de cache, l’élément racine de la requête est ensuite disponible à partir de la propriété <xref:System.Windows.Automation.AutomationElement.CachedParent%2A> de chacun des éléments enfants.  
  
> [!NOTE]
> Vous ne pouvez pas mettre en cache les parents ou les ancêtres de l’élément racine de la requête.  
  
<a name="Updating_the_Cache"></a>
## <a name="updating-the-cache"></a>Mise à jour du cache  
 Le cache reste valide tant que rien ne change dans l’ [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]. Votre application est responsable de la mise à jour du cache, généralement en réponse à des événements.  
  
 Si vous vous abonnez à un événement quand un <xref:System.Windows.Automation.CacheRequest> est actif, vous obtenez un <xref:System.Windows.Automation.AutomationElement> avec un cache mis à jour comme source de l’événement chaque fois que votre délégué de gestionnaire d’événements est appelé. Vous pouvez également mettre à jour les informations mises en cache d’un élément en appelant <xref:System.Windows.Automation.AutomationElement.GetUpdatedCache%2A>. Vous pouvez passer le <xref:System.Windows.Automation.CacheRequest> d’origine pour mettre à jour toutes les informations précédemment mises en cache.  
  
 La mise à jour du cache n’altère pas les propriétés des références <xref:System.Windows.Automation.AutomationElement> existantes.  
  
## <a name="see-also"></a>Voir aussi

- [Événements UI Automation pour les clients](ui-automation-events-for-clients.md)
- [Utiliser la mise en cache dans UI Automation](use-caching-in-ui-automation.md)
- [Exemple FetchTimer](/previous-versions/dotnet/netframework-3.5/ms771456(v=vs.90))
