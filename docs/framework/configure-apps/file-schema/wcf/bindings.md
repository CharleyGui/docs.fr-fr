---
title: <bindings>
ms.date: 01/22/2018
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: fe8f620668e35183890b8bba1f254a74c962f8d3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139666"
---
# \<bindings>

Vous pouvez utiliser l' `bindings` élément pour configurer une collection de liaisons standard et personnalisées pour Windows Communication Foundation (WCF). Chaque entrée est un élément de `binding` qui peut être identifié par son `name` unique. Les services utilisent les liaisons en les liant à l’aide de `name`. À compter de .NET Framework 4, les liaisons et les comportements n’ont pas besoin d’un nom. Pour plus d’informations sur la configuration par défaut et les liaisons et les comportements sans valeur, consultez [configuration simplifiée](../../../wcf/simplified-configuration.md) et [configuration simplifiée pour les services WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).

## <a name="system-provided-bindings"></a>Liaisons fournies par le système

Les liaisons fournies par le système masquent la complexité de la pile de la messagerie du WCF. Les applications qui utilisent des liaisons fournies par le système ne requièrent pas de contrôle total sur la pile. Les attributs exposés sur chaque liaison fournie par le système sont les plus appropriés pour le scénario d'utilisation des adresses de liaison.

La section de configuration de chaque liaison fournie par le système peut définir plusieurs configurations utilisées en vue de configurer la liaison. Chaque configuration est identifiée par un nom unique.

Il n’est pas possible d’ajouter des éléments ou des attributs à une liaison fournie par le système. Pour ce faire, vous devez implémenter une liaison personnalisée comme décrit dans la section [liaisons personnalisées](#custom-bindings) . Il est possible de définir une liaison personnalisée qui imite parfaitement une liaison fournie par le système et ajoute quelques paramètres sur lesquels l’application utilisateur souhaite avoir le contrôle.  

Pour obtenir la liste des liaisons fournies par le système, consultez [liaisons fournies par le système](../../../wcf/system-provided-bindings.md).

## <a name="custom-bindings"></a>Liaisons personnalisées

Les liaisons personnalisées permettent d'exercer un contrôle total sur la pile de messagerie WCF. Une liaison individuelle définit la pile de messages en spécifiant les éléments de configuration des éléments de la pile suivant leur l'ordre d'apparition dans cette pile. Chaque élément définit et configure un élément de la pile. Il doit y avoir un seul élément de `transport` dans chaque liaison personnalisée. Sans cet élément, la pile de messagerie est incomplète.

L'ordre dans lequel les éléments apparaissent dans la pile est important car il s'agit de l'ordre dans lequel les opérations sont appliquées au message. Voici l'ordre requis des éléments de la pile :  

1. Transactions (facultatif)  

2. Messagerie fiable (facultatif)  

3. Sécurité (facultatif)  

4. Encodeur  

5. Transport  

 Les liaisons personnalisées sont identifiées par leur attribut `name`. Pour plus d’informations sur les liaisons personnalisées, consultez [liaisons personnalisées](../../../wcf/extending/custom-bindings.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Configuration.BindingsSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>
- [Liaisons](../../../wcf/bindings.md)
- [Liaisons personnalisées](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
