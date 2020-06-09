---
title: Création de services WCF pour ASP.NET AJAX
ms.date: 03/30/2017
ms.assetid: 04c0402c-e617-4ba5-aedf-d17692234776
ms.openlocfilehash: 8c82d4c61b32572fd1ad7d8f19e939273cc2280b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599306"
---
# <a name="creating-wcf-services-for-aspnet-ajax"></a>Création de services WCF pour ASP.NET AJAX

Microsoft ASP.NET AJAX permet de créer rapidement des pages Web d'une grande interaction pour l'utilisateur avec des éléments d'interface utilisateur réactifs et familiers. Les fonctionnalités ASP.NET AJAX fournissent des bibliothèques de client de script qui incorporent des scripts ECMAScript (JavaScript) et des technologies Dynamic HTML (DHTML) compatibles entre navigateurs ainsi qu'une intégration avec la plate-forme de développement serveur ASP.NET 2.0. Grâce à ASP.NET AJAX, vous pouvez améliorer l'expérience utilisateur et l'efficacité de vos applications Web.

ASP.NET AJAX se compose de bibliothèques de client de script et des composants serveur intégrés destinés à fournir une infrastructure de développement fiable. Pour accéder à un service à partir d'une page ASP.NET : une fois que l'URL de service est ajoutée au contrôle de gestionnaire de script ASP.NET dans la page, les opérations de service peuvent être appelées à l'aide du code Javascript qui est identique à un appel de fonction JavaScript régulier.

La plupart des services Windows Communication Foundation (WCF) peuvent être exposés en tant que service compatible avec ASP.NET AJAX en ajoutant un point de terminaison ASP.NET AJAX approprié.

Si vous utilisez Visual Studio, vous pouvez utiliser un modèle prédéfini pour les services WCF compatibles AJAX, disponible dans la boîte de dialogue **Ajouter un nouvel élément** lorsque vous travaillez avec des sites Web ou des Applications Web ASP.net.

Si vous n'utilisez pas les modèles Visual Studio, vous pouvez créer un point de terminaison ASP.NET AJAX de deux manières :

- Créez le point de terminaison à l'aide de l'activation d'hôte dynamique sans utiliser de configuration. Il s'agit de l'approche la plus simple si vous n'êtes pas familier avec le système de configuration WCF. Pour plus d’informations, consultez [Comment : ajouter un point de terminaison ASP.NET AJAX sans utiliser la configuration](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).

- Ajoutez un point de terminaison compatible AJAX à un service WCF à l’aide de la configuration. Pour plus d’informations, consultez [Comment : utiliser la configuration pour ajouter un point de terminaison AJAX ASP.net](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).

Le modèle de programmation Web décrit dans la [vue d’ensemble du modèle de programmation http Web WCF](wcf-web-http-programming-model-overview.md) peut être utilisé avec les services ASP.NET AJAX. Plus précisément :

- Vous pouvez utiliser les attributs <xref:System.ServiceModel.Web.WebGetAttribute> et <xref:System.ServiceModel.Web.WebInvokeAttribute> pour choisir entre les verbes HTTP GET et HTTP POST. Correctement utilisés, ils permettent d'améliorer considérablement la performance de votre application. Pour plus d’informations, consultez [Comment : choisir entre des demandes HTTP http et http pour les points de terminaison ASP.NET AJAX](http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md).

- Vous pouvez utiliser les propriétés <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> et <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> pour que votre service retourne des données XML au lieu du format JSON (JavaScript Object Notation) par défaut. Effectuée dans le cadre de l'infrastructure ASP.NET AJAX, cette opération permet au client JavaScript de recevoir un objet XML DOM.

  > [!WARNING]
  > Votre opération doit affecter au type de contenu la valeur texte/xml pour y parvenir. Sinon, le client JavaScript recevra une chaîne contenant le XML au lieu d'un objet XML DOM.

    Voici un exemple d'opération qui retourne les données XML avec le type de contenu défini convenablement :

  ```csharp
  [OperationContract, WebGet(ResponseFormat=WebMessageFormat.Xml)]
  public XElement GetData()
  {
      XElement x;
      //Get some data here...

      WebOperationContext.Current.OutgoingResponse.ContentType = "text/xml";
      return x;
  }
  ```

- Aucune autre propriété sur les attributs <xref:System.ServiceModel.Web.WebGetAttribute> et <xref:System.ServiceModel.Web.WebInvokeAttribute> ne peut être modifiée si la compatibilité avec ASP.NET AJAX est requise. Il est possible de faire appel à d'autres aspects du modèle de programmation Web tant que les conventions d'appel ASP.NET AJAX sont respectées.

 Des scénarios plus avancés requièrent des détails supplémentaires sur la prise en charge d’AJAX dans WCF :

- Pour comprendre comment les données sont transférées entre un client de page AJAX et un service WCF à l’aide de JavaScript, et pour plus d’informations sur la façon dont les types de .NET Framework sont mappés aux types JavaScript, consultez [prise en charge de JSON et d’autres formats de transfert de données](support-for-json-and-other-data-transfer-formats.md).

- Pour tirer parti des fonctionnalités ASP.NET, par exemple, l’authentification basée sur URL et l’accès aux informations de session ASP.NET, vous pouvez activer le mode de compatibilité ASP.NET par la configuration.

Les points de terminaison AJAX dans WCF peuvent même être consommés sans l’infrastructure AJAX ASP.NET. Pour ce faire, vous devez comprendre l’architecture de prise en charge de la prise en charge d’AJAX dans WCF. Pour une description de cette architecture, consultez [modèle objet de programmation http Web WCF](wcf-web-http-programming-object-model.md). Pour obtenir un exemple de code illustrant cette approche, consultez le [service Ajax avec JSON et XML](../samples/ajax-service-with-json-and-xml-sample.md).

## <a name="see-also"></a>Voir aussi

- [Modèle de programmation HTTP Web WCF](wcf-web-http-programming-model.md)
- [Guide pratique pour ajouter un point de terminaison AJAX ASP.NET sans utiliser de configuration](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)
- [Comment : utiliser la configuration pour ajouter un point de terminaison AJAX ASP.NET](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)
- [Comment : choisir entre des demandes HTTP POST et HTTP GET pour des points de terminaison AJAX ASP.NET](http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)
