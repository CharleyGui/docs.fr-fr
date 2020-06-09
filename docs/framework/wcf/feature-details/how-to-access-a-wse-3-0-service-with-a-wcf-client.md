---
title: 'Comment : accéder à un service WSE 3.0 avec un client WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f9bcd9b-8f8f-47fa-8f1e-0d47236eb800
ms.openlocfilehash: 179591c272685771fbde12e161cb38b1bd969052
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597200"
---
# <a name="how-to-access-a-wse-30-service-with-a-wcf-client"></a>Comment : accéder à un service WSE 3.0 avec un client WCF
Les clients Windows Communication Foundation (WCF) sont compatibles au niveau du câble avec les améliorations apportées aux services Web (WSE) 3,0 pour les services Microsoft .NET lorsque les clients WCF sont configurés pour utiliser la version du 2004 d’août de la spécification WS-Addressing. Toutefois, les services WSE 3,0 ne prennent pas en charge le protocole MEX (Metadata Exchange). par conséquent, lorsque vous utilisez l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) pour créer une classe de client WCF, les paramètres de sécurité ne sont pas appliqués au client WCF généré. Par conséquent, vous devez spécifier les paramètres de sécurité requis par le service WSE 3,0 après la génération du client WCF.  
  
 Vous pouvez appliquer ces paramètres de sécurité à l’aide d’une liaison personnalisée pour prendre en compte les exigences du service WSE 3,0 et les exigences interopérables entre un service WSE 3,0 et un client WCF. Ces exigences d’interopérabilité incluent l’utilisation précédemment mentionnée de la version d’août 2004 de la spécification WS-Addressing et la protection des messages par défaut WSE 3.0 de <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>. La protection par défaut des messages pour WCF est <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature> . Cette rubrique explique en détail comment créer une liaison WCF qui interagit avec un service WSE 3,0. WCF fournit également un exemple qui incorpore cette liaison. Pour plus d’informations sur cet exemple, consultez [interopérabilité avec les services Web ASMX](../samples/interoperating-with-asmx-web-services.md).  
  
### <a name="to-access-a-wse-30-web-service-with-a-wcf-client"></a>Pour accéder à un service Web WSE 3.0 avec un client WCF  
  
1. Exécutez l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) pour créer un client WCF pour le service Web WSE 3,0.  
  
     Pour un service Web WSE 3,0, un client WCF est créé. WSE 3.0 ne prenant pas en charge le protocole MEX, vous ne pouvez pas utiliser l'outil pour récupérer les conditions de sécurité pour le service Web. Le développeur d'applications doit ajouter les paramètres de sécurité pour le client.  
  
     Pour plus d’informations sur la création d’un client WCF, consultez la rubrique [Comment : créer un client](../how-to-create-a-wcf-client.md).  
  
2. Créez une classe qui représente une liaison pouvant communiquer avec les services Web WSE 3.0.  
  
     La classe suivante fait partie de l’exemple [interopérabilité avec WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29) :  
  
    1. Créez une classe qui dérive de la classe <xref:System.ServiceModel.Channels.Binding>.  
  
         L'exemple de code suivant crée une classe nommée `WseHttpBinding` qui dérive de la classe <xref:System.ServiceModel.Channels.Binding>.  
  
         [!code-csharp[c_WCFClientToWSEService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#1)]
         [!code-vb[c_WCFClientToWSEService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#1)]  
  
    2. Ajoutez à la classe des propriétés spécifiant l'assertion clé en main WSE utilisée par le service WSE, si des clés dérivées sont requises, si des sessions sécurisées sont utilisées, si des confirmations de signature sont requises, ainsi que les paramètres de protection des messages. Dans WSE 3,0, une assertion clé en main spécifie les exigences de sécurité pour un client ou un service Web, similaire au mode d’authentification d’une liaison dans WCF.  
  
         L'exemple de code suivant définit les propriétés `SecurityAssertion`, `RequireDerivedKeys`, `EstablishSecurityContext` et `MessageProtectionOrder` qui spécifient l'assertion clé en main WSE, si des clés dérivées sont requises, si des sessions sécurisées sont utilisées, si des confirmations de signature sont requises, ainsi que les paramètres de protection des messages, respectivement.  
  
         [!code-csharp[c_WCFClientToWSEService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#3)]
         [!code-vb[c_WCFClientToWSEService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#3)]  
  
    3. Substituez la méthode <xref:System.ServiceModel.Channels.Binding.CreateBindingElements%2A> pour définir les propriétés de la liaison.  
  
         L'exemple de code suivant spécifie le transport, l'encodage de message et les paramètres de protection des messages en obtenant les valeurs des propriétés `SecurityAssertion` et `MessageProtectionOrder`.  
  
         [!code-csharp[c_WCFClientToWSEService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/wsehttpbinding.cs#2)]
         [!code-vb[c_WCFClientToWSEService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/wsehttpbinding.vb#2)]  
  
3. Dans le code d’application cliente, ajoutez le code pour définir les propriétés de la liaison.  
  
     L’exemple de code suivant spécifie que le client WCF doit utiliser la protection des messages et l’authentification comme défini par l' `AnonymousForCertificate` assertion de sécurité clé en main WSE 3,0. En outre, des sessions sécurisées et des clés dérivées sont requises.  
  
     [!code-csharp[c_WCFClientToWSEService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wcfclienttowseservice/cs/client.cs#4)]
     [!code-vb[c_WCFClientToWSEService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wcfclienttowseservice/vb/client.vb#4)]  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant définit une liaison personnalisée qui expose des propriétés correspondant à celles d'une assertion de sécurité clé en main WSE 3.0. Cette liaison personnalisée, qui est nommée `WseHttpBinding` , est ensuite utilisée pour spécifier les propriétés de liaison d’un client WCF qui communique avec l’exemple de démarrage rapide WSSECURITYANONYMOUS WSE 3,0.  

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Channels.Binding>
- [Interoperating with WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752257%28v=vs.90%29)
