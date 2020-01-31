---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: fdd6d83836c4ef31a4d7c8e68cb0cc050ac6bea4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76787798"
---
# <a name="servicehost"></a>\@ServiceHost

Associe la fabrique utilisée pour générer l'hôte de service au service à héberger ainsi qu'à d'autres aspects de programmation requis pour compiler le code d'hébergement fourni dans le fichier .svc ou pour y accéder.

## <a name="syntax"></a>Syntaxe

```xml
<% @ServiceHost
Service = "Service, ServiceNamespace"
Factory = "Factory, FactoryNamespace"
Debug = "Debug"
Language = "Language"
CodeBehind = "CodeBehind"
%>
```

## <a name="attributes"></a>Attributs

### <a name="service"></a>Service

Nom de type CLR du service hébergé. Il doit s'agir d'un nom qualifié correspondant à un type qui implémente un ou plusieurs contacts du service.

### <a name="factory"></a>Fabrique

Nom de type CLR correspondant à la fabrique de l'hôte de service utilisée pour instancier l'hôte de service. Cet attribut est facultatif. S'il n'est pas spécifié, le <xref:System.ServiceModel.Activation.ServiceHostFactory> par défaut est utilisé et renvoie une instance de <xref:System.ServiceModel.ServiceHost>.

### <a name="debug"></a>Déboguer

Indique si le service Windows Communication Foundation (WCF) doit être compilé avec des symboles de débogage. `true` si le service WCF doit être compilé avec des symboles de débogage ; Sinon, `false`.

### <a name="language"></a>Language

Spécifie le langage utilisé lors de la compilation de l'intégralité du code incorporé dans le fichier (.svc). Les valeurs peuvent représenter any. Langage NET-pris en charge, y compris `C#`, `VB`et `JS`, qui C#font respectivement référence à, Visual Basic et JScript .net. Cet attribut est facultatif.

### <a name="codebehind"></a>CodeBehind

Spécifie le fichier source qui implémente le service Web XML, lorsque la classe qui implémente le service Web XML ne réside pas dans le même fichier et n’a pas été compilée dans un assembly et placée dans le répertoire *\Bin* .

## <a name="remarks"></a>Notes

Le <xref:System.ServiceModel.ServiceHost> utilisé pour héberger le service est un point d’extensibilité au sein du modèle de programmation Windows Communication Foundation (WCF). Un modèle de fabrique est utilisé pour instancier le <xref:System.ServiceModel.ServiceHost> car il peut s'agir d'un type polymorphe ne devant pas être instancié directement par l'environnement d'hébergement.

L'implémentation par défaut utilise <xref:System.ServiceModel.Activation.ServiceHostFactory> pour créer une instance de <xref:System.ServiceModel.ServiceHost>. Toutefois, vous pouvez fournir votre propre fabrique (un qui retourne votre hôte dérivé) en spécifiant le nom de type CLR de votre implémentation de fabrique dans la directive `@ServiceHost`.

Pour utiliser votre propre fabrique d’hôte de service personnalisée au lieu de la fabrique par défaut, il vous suffit de fournir le nom de type dans la directive `@ServiceHost` comme suit.

```xml
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>
```

Surchargez les implémentations de fabrique le moins possible. Si vous disposez d'une importante logique personnalisée, votre code est plus facilement réutilisable si vous intégrez cette logique à votre hôte et non à la fabrique.

Par exemple, pour activer un point de terminaison compatible AJAX pour `MyService`, spécifiez le <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> pour la valeur de l’attribut `Factory`, au lieu du <xref:System.ServiceModel.Activation.ServiceHostFactory>par défaut, dans la directive `@ServiceHost`, comme indiqué dans l’exemple suivant :

```xml
<% @ServiceHost
Service="MyService"
Language="C#"
Debug="true"
Factory="WebScriptServiceHostFactory"
%>
```

## <a name="see-also"></a>Voir aussi

- [Hôte de service personnalisé](../../../wcf/samples/custom-service-host.md)
