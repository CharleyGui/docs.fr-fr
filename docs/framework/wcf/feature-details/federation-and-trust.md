---
title: Fédération et confiance
ms.date: 03/30/2017
helpviewer_keywords:
- federation [WCF], and trust
ms.assetid: 4bdec4f2-f8a2-4512-bdcf-14ef54b5877a
ms.openlocfilehash: 6baa336f96f2349315cab2ed51bfb67c4745a110
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255479"
---
# <a name="federation-and-trust"></a>Fédération et confiance

Cette rubrique aborde différents aspects liés aux applications fédérées, aux limites d’approbation et à la configuration, ainsi qu’à l’utilisation de jetons émis dans Windows Communication Foundation (WCF).  
  
## <a name="services-security-token-services-and-trust"></a>Services, services d'émission de jeton de sécurité et confiance  

 Les services qui exposent des points de terminaison fédérés s'attendent en général à ce que les clients s'authentifient à l'aide d'un jeton fourni par un émetteur spécifique. Il est important que le service soit configuré avec les informations d'identification correctes de l'émetteur ; dans le cas contraire, il ne sera pas en mesure de vérifier les signatures sur les jetons émis, et le client ne pourra pas communiquer avec le service. Pour plus d’informations sur la configuration des informations d’identification de l’émetteur sur le service, consultez [procédure : configurer les informations d’identification sur un service FS (Federation Service)](how-to-configure-credentials-on-a-federation-service.md).  
  
 De la même façon, lorsque vous utilisez des clés symétriques, les clés sont chiffrées pour le service cible et vous devez donc configurer le service d'émission de jeton de sécurité avec les informations d'identification correctes du service cible ; dans le cas contraire, il ne sera pas en mesure de chiffrer la clé pour le service cible, et une nouvelle fois, le client ne pourra pas communiquer avec le service.  
  
 Les services WCF utilisent la valeur de la <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> propriété sur le [SecurityBindingElement](../diagnostics/wmi/securitybindingelement.md) pour autoriser l’inclinaison de l’horloge entre le client et le service. Dans la fédération, le paramètre `MaxClockSkew` s'applique aux inclinaisons de l'horloge entre à la fois le client et le service d'émission de jeton de sécurité à partir duquel le client a obtenu le jeton émis. Par conséquent, les services d'émission de jeton de sécurité n'ont pas besoin d'allouer d'inclinaison d'horloge lors de la définition des délais de validité et d'expiration du jeton émis.  
  
> [!NOTE]
> L'importance de l'inclinaison de l'horloge augmente à mesure que la durée de vie du jeton émis raccourcit. Dans la plupart des cas, l'inclinaison de l'horloge n'est pas un problème significatif si la durée de vie du jeton est de 30 minutes ou plus. Des scénarios avec des durées de vie plus courtes ou dans lesquels le délai de validité exact du jeton est important doivent être conçus afin de prendre l'inclinaison de l'horloge en compte.  
  
## <a name="federated-endpoints-and-time-outs"></a>Points de terminaison fédérés et délais d'expiration  

 Lorsqu'un client communique avec un point de terminaison fédéré, il doit tout d'abord acquérir un jeton approprié d'un service d'émission de jeton de sécurité. Si le service d'émission de jeton de sécurité expose un point de terminaison fédéré, le client doit en premier lieu obtenir un jeton de l'émetteur pour ce point de terminaison. Chaque acquisition de jeton prend du temps, et ce temps est soumis au délai d'expiration total pour l'envoi du message réel au point de terminaison final.  
  
 Par exemple, le délai d'expiration sur le canal côté client a pour valeur 30 secondes. Deux émetteurs de jeton doivent être appelés pour récupérer des jetons avant d'envoyer le message au point de terminaison final, et chacun prend 15 secondes pour émettre un jeton. Dans ce cas, la tentative échoue et une exception <xref:System.TimeoutException> est levée. Vous devez donc définir <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A> sur le canal client à une valeur suffisamment élevée pour inclure le temps pris pour récupérer tous les jetons émis. Si aucune valeur n'est spécifiée pour la propriété <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A>, la propriété <xref:System.ServiceModel.Channels.Binding.OpenTimeout%2A> ou la propriété <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A> (ou les deux) doivent avoir une valeur suffisamment élevée pour inclure le temps pris pour récupérer tous les jetons émis.  
  
## <a name="token-lifetime-and-renewal"></a>Renouvellement et durée de vie des jetons  

 Les clients WCF ne vérifient pas le jeton émis lors de la demande initiale à un service.  Au lieu de cela, WCF approuve le service d’émission de jeton de sécurité pour émettre un jeton avec les délais d’expiration et effectifs appropriés. Si le jeton est mis en cache par le client et réutilisé, sa durée de vie est vérifiée sur les demandes suivantes, et le client le renouvelle automatiquement si nécessaire. Pour plus d’informations sur la mise en cache des jetons, consultez [procédure : création d’un client fédéré](how-to-create-a-federated-client.md).  
  
 La spécification de durées de vie courtes, sur l’ordre de 30 secondes ou moins pour les jetons émis ou les jetons de contexte de sécurité, peut entraîner des délais d’expiration de négociation ou d’autres exceptions générées par les clients WCF lors de la demande de jetons émis ou lors de la négociation ou du renouvellement des jetons de contexte de sécurité.  
  
## <a name="issued-tokens-and-inclusionmode"></a>Jetons émis et InclusionMode  

 Qu'un jeton émis soit ou non sérialisé dans un message envoyé d'un client vers un point de terminaison fédéré, il est contrôlé en définissant la propriété <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.InclusionMode%2A> de la classe <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters>. Cette propriété peut prendre l'une des valeurs de l'énumération <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>, mais ce n'est pas utile dans la plupart des scénarios fédérés. Les valeurs `SecurityTokenInclusionMode.Never` et `SecurityTokenInclusionMode.AlwaysToInitiator` provoquent l'envoi par le client d'une référence au jeton émis par le service d'émission de jeton de sécurité à la partie de confiance. Sauf si la partie de confiance possède une copie du jeton émis, l'authentification échouera car la référence du jeton ne peut pas être résolue. WCF traite `SecurityTokenInclusionMode.Once` comme équivalent à `SecurityTokenInclusionMode.AlwaysToRecipient` .  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>
- [Procédure : créer un client fédéré](how-to-create-a-federated-client.md)
- [Procédure : configurer des informations d’identification sur un service de fédération](how-to-configure-credentials-on-a-federation-service.md)
- [Procédure : créer un WSFederationHttpBinding](how-to-create-a-wsfederationhttpbinding.md)
