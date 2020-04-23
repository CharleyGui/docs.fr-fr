---
title: Considérations sur la sécurité XAML
ms.date: 03/30/2017
helpviewer_keywords:
- security [XAML Services], .NET XAML services
- XAML security [XAML Services]
ms.assetid: 544296d4-f38e-4498-af49-c9f4dad28964
ms.openlocfilehash: 1864910b339c74e3033fb4d6d8baebffada1a4f8
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071688"
---
# <a name="xaml-security-considerations"></a>Considérations de sécurité XAML

Cet article décrit les meilleures pratiques de sécurité dans les applications lorsque vous utilisez XAML et .NET XAML Services API.

## <a name="untrusted-xaml-in-applications"></a>XAML non fiable dans les applications

Dans le sens le plus général, XAML non fiable est toute source XAML que votre application n’a pas spécifiquement inclure ou émettre.

XAML qui est compilé ou `resx`stocké comme une ressource de type dans un assemblage de confiance et signé n’est pas intrinsèquement non fiable. Vous pouvez faire confiance au XAML autant que vous faites confiance à l’assemblage dans son ensemble. Dans la plupart des cas, vous n’êtes concerné que par les aspects de confiance de XAML lâche, qui est une source XAML que vous chargez à partir d’un flux ou d’autres I / O. Loose XAML n’est pas un composant ou une fonctionnalité spécifique d’un modèle d’application avec une infrastructure de déploiement et d’emballage. Cependant, un assemblage peut mettre en œuvre un comportement qui implique le chargement lâche XAML.

Pour XAML non fiable, vous devez le traiter généralement de la même façon que s’il s’agissait d’un code non fiable. Utilisez le bac à sable ou d’autres métaphores pour empêcher XAML, qui n’est peut-être pas fiable, d’accéder à votre code de confiance.

La nature des capacités XAML donne au XAML le droit de construire des objets et de définir leurs propriétés. Ces capacités comprennent également l’accès aux convertisseurs de type, la cartographie `x:Code` et l’accès aux assemblages dans le domaine de l’application, en utilisant des extensions de balisage, des blocs, et ainsi de suite.

En plus de ses capacités linguistiques, XAML est utilisé pour la définition de l’interface utilisateur dans de nombreuses technologies. Le chargement de XAML non fiable peut signifier le chargement d’une interface utilisateur malveillante usurpant.

## <a name="sharing-context-between-readers-and-writers"></a>Partager le contexte entre les lecteurs et les écrivains

.NET XAML Services architecture pour les lecteurs XAML et les écrivains XAML nécessite souvent de partager un lecteur XAML à un écrivain XAML, ou un contexte de schéma XAML partagé. Le partage d’objets ou de contextes peut être nécessaire si vous écrivez la logique de boucle de nœud XAML, ou si vous fournissez un chemin d’enregistrement personnalisé. Ne partagez pas les instances des lecteurs XAML, le contexte du schéma XAML non responsable ou les paramètres des cours de lecteur/écrivain XAML entre le code de confiance et le code non fiable.

La plupart des scénarios et des opérations impliquant l’écriture d’objets XAML pour un support de type CLR peut simplement utiliser le contexte de schéma XAML par défaut. Le contexte du schéma XAML par défaut n’inclut pas explicitement les paramètres qui pourraient compromettre la pleine confiance. Il est donc sûr de partager le contexte entre les composants fiables et non fiables de lecteur/écrivain de XAML. Cependant, si vous faites cela, il est toujours une pratique <xref:System.AppDomain> exemplaire de garder ces lecteurs et écrivains dans des portées distinctes, avec l’un d’eux spécifiquement destiné / sandboxed pour la confiance partielle.

## <a name="xaml-namespaces-and-assembly-trust"></a>XAML Namespaces et Assembly Trust

La syntaxe et la définition non qualifiées de base pour la façon dont XAML interprète une cartographie personnalisée XAML namespace à un assemblage ne fait pas de distinction entre un assemblage de confiance et un assemblage non fiable tel qu’il est chargé dans le domaine de l’application. Ainsi, il est techniquement possible pour un assemblage non fiable d’usurper la cartographie XAML d’un espace de nom de l’assemblage de confiance et de capturer les informations déclarées sur les objets et les biens d’une source XAML. Si vous avez des exigences de sécurité pour éviter cette situation, votre cartographie de l’espace de nom XAML prévue doit être faite en utilisant l’une des techniques suivantes :

- Utilisez un nom d’assemblage entièrement qualifié avec un nom fort dans n’importe quelle cartographie XAML namespace faite par XAML de votre application.

- Limitez la cartographie d’assemblage à un ensemble <xref:System.Xaml.XamlSchemaContext> fixe d’assemblages de référence, en construisant un spécifique pour vos lecteurs XAML et les auteurs d’objets XAML. Consultez <xref:System.Xaml.XamlSchemaContext.%23ctor%28System.Collections.Generic.IEnumerable%7BSystem.Reflection.Assembly%7D%29>.

## <a name="xaml-type-mapping-and-type-system-access"></a>XAML Type Mapping and Type System Access

XAML prend en charge son propre système de type, qui à bien des égards est un pair à la façon dont CLR implémente le système de base de type CLR. Toutefois, pour certains aspects de la sensibilisation au type où vous prendrez des décisions de confiance au sujet d’un type d’information de type, vous devriez vous en remettre aux informations de type dans les types de support CLR. C’est parce que certaines des capacités de reporting spécifiques du système de type XAML sont laissées ouvertes comme méthodes virtuelles et ne sont donc pas entièrement sous le contrôle des implémentations originales .NET XAML Services. Ces points d’extabilité existent parce que le système de type XAML est extensible, pour correspondre à l’extéabilité de XAML lui-même et à ses stratégies alternatives possibles de cartographie de type par rapport à la mise en œuvre par défaut soutenu par CLR et par défaut XAML contexte schéma. Pour plus d’informations, voir les notes <xref:System.Xaml.XamlType> <xref:System.Xaml.XamlMember>spécifiques sur plusieurs des propriétés de et .

## <a name="see-also"></a>Voir aussi

- <xref:System.Xaml.Permissions.XamlAccessLevel>
