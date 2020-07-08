---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: cb425d9f4dadd97e93946a2b4cd9d059ea8504ce
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051361"
---
# <a name="servicehost"></a>\@ServiceHost

Associe la fabrique utilisée pour générer l'hôte de service au service à héberger ainsi qu'à d'autres aspects de programmation requis pour compiler le code d'hébergement fourni dans le fichier .svc ou pour y accéder.

## <a name="syntax"></a>Syntax

```aspx-csharp
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

### <a name="debug"></a>Débogage

Indique si le service Windows Communication Foundation (WCF) doit être compilé avec des symboles de débogage. `true`Si le service WCF doit être compilé avec des symboles de débogage ; Sinon, `false` .

### <a name="language"></a>Langage

Spécifie le langage utilisé lors de la compilation de l'intégralité du code incorporé dans le fichier (.svc). Les valeurs peuvent représenter any. Langage NET-pris en charge, notamment `C#` ,, `VB` et `JS` , qui font respectivement référence à C#, Visual Basic et JScript .net. Cet attribut est facultatif.

### <a name="codebehind"></a>CodeBehind

Spécifie le fichier source qui implémente le service Web XML, lorsque la classe qui implémente le service Web XML ne réside pas dans le même fichier et n’a pas été compilée dans un assembly et placée dans le répertoire *\Bin* .

## <a name="remarks"></a>Remarques

Le <xref:System.ServiceModel.ServiceHost> utilisé pour héberger le service est un point d’extensibilité au sein du modèle de programmation Windows Communication Foundation (WCF). Un modèle de fabrique est utilisé pour instancier le <xref:System.ServiceModel.ServiceHost> car il peut s'agir d'un type polymorphe ne devant pas être instancié directement par l'environnement d'hébergement.

L'implémentation par défaut utilise <xref:System.ServiceModel.Activation.ServiceHostFactory> pour créer une instance de <xref:System.ServiceModel.ServiceHost>. Toutefois, vous pouvez fournir votre propre fabrique (un qui retourne votre hôte dérivé) en spécifiant le nom de type CLR de votre implémentation de fabrique dans la `@ServiceHost` directive.

Pour utiliser votre propre fabrique d’hôte de service personnalisée au lieu de la fabrique par défaut, il vous suffit de fournir le nom de type dans la `@ServiceHost` directive comme suit.

```xml
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>
```

Surchargez les implémentations de fabrique le moins possible. Si vous disposez d'une importante logique personnalisée, votre code est plus facilement réutilisable si vous intégrez cette logique à votre hôte et non à la fabrique.

Par exemple, pour activer un point de terminaison compatible AJAX pour `MyService` , spécifiez <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> pour la valeur de l' `Factory` attribut, au lieu de la valeur par défaut <xref:System.ServiceModel.Activation.ServiceHostFactory> , dans la `@ServiceHost` directive, comme indiqué dans l’exemple suivant :

```aspx-csharp
<% @ServiceHost
Service="MyService"
Language="C#"
Debug="true"
Factory="WebScriptServiceHostFactory"
%>
```

## <a name="see-also"></a>Voir aussi

- [Custom Service Host](../../../wcf/samples/custom-service-host.md)
