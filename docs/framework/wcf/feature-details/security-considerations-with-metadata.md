---
title: Considérations sur la sécurité des métadonnées
ms.date: 03/30/2017
ms.assetid: e78ef8ab-4f63-4656-ab93-b1deab2666d5
ms.openlocfilehash: c7a00d5abc9cc88b60208bd76fa8874f1fe00af9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275994"
---
# <a name="security-considerations-with-metadata"></a>Considérations sur la sécurité des métadonnées

Lorsque vous utilisez les fonctionnalités de métadonnées dans Windows Communication Foundation (WCF), tenez compte des implications en matière de sécurité de la publication, de la récupération et de l’utilisation des métadonnées de service.  
  
## <a name="when-to-publish-metadata"></a>Quand publier des métadonnées  

 Les services WCF ne publient pas de métadonnées par défaut. Pour publier des métadonnées pour un service WCF, vous devez activer explicitement la publication de métadonnées en ajoutant des points de terminaison de métadonnées à votre service (consultez [publication de métadonnées](publishing-metadata.md)). Désactiver la publication de métadonnées permet de réduire la surface d'attaque de votre service et limiter le risque de divulgation d'informations involontaire. Tous les services ne sont pas tenus de publier des métadonnées. Si vous n'avez pas besoin de publier de métadonnées, laissez cette fonctionnalité désactivée. Notez que vous pouvez toujours générer des métadonnées et du code client directement à partir de vos assemblys de service à l’aide de l' [outil utilitaire de métadonnées ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md). Pour plus d’informations sur l’utilisation de Svcutil.exe pour exporter des métadonnées, consultez [Comment : utiliser Svcutil.exe pour exporter des métadonnées à partir du code de service compilé](how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md).  
  
## <a name="publishing-metadata-using-a-secure-binding"></a>Publication de métadonnées à l'aide d'une liaison sécurisée  

 Les liaisons de métadonnées par défaut fournies par WCF ne sont pas sécurisées et elles autorisent l’accès anonyme aux métadonnées. Les métadonnées de service publiées par un service WCF contiennent une description détaillée du service et peuvent, intentionnellement ou non, contenir des informations sensibles. Par exemple, des métadonnées de service peuvent contenir des informations sur des opérations d'infrastructure qui n'étaient pas destinées à être diffusées publiquement. Pour protéger des métadonnées de service contre les accès non autorisés, vous pouvez recourir à une liaison sécurisée pour le point de terminaison des métadonnées. Les points de terminaison de métadonnées répondent à des demandes HTTP/GET qui peuvent utiliser le protocole SSL (Secure Sockets Layer) pour sécuriser les métadonnées. Pour plus d’informations, consultez [Comment : sécuriser des points de terminaison de métadonnées](how-to-secure-metadata-endpoints.md).  
  
 La sécurisation des points de terminaison de métadonnées permet aussi de fournir aux demandeurs un moyen de récupérer en toute sécurité les métadonnées de service sans risque de falsification ou d'usurpation.  
  
## <a name="using-only-trusted-metadata"></a>Utilisation de métadonnées approuvées uniquement  

 Les métadonnées de service permettent de construire automatiquement les composants d'exécution requis pour appeler le service. Vous pouvez également utiliser des métadonnées au moment du design, pour développer une application cliente, ou au moment de l'exécution, pour mettre à jour de manière dynamique la liaison qu'un client utilise pour appeler un service.  
  
 Les métadonnées de service peuvent être falsifiées ou usurpées lorsqu'elles sont récupérées de façon non sécurisée. Des métadonnées falsifiées sont susceptibles de rediriger votre client vers un service malveillant ou de contenir des paramètres de sécurité compromis ou des structures XML nuisibles. Les documents de métadonnées peuvent être volumineux et sont souvent enregistrés dans le système de fichiers. Pour vous protéger contre la falsification et l’usurpation de données, utilisez une liaison sécurisée pour demander des métadonnées de service, lorsque ce type de liaison est disponible.  
  
## <a name="using-safe-techniques-for-processing-metadata"></a>Utilisation de techniques éprouvées pour traiter les métadonnées  

 Les métadonnées de service sont souvent récupérées d'un service situé sur un réseau à l'aide de protocoles standardisés, tels que WS-MetadataExchange (MEX). De nombreux formats de métadonnées incluent des mécanismes de référencement pour pointer vers des métadonnées supplémentaires. Le type <xref:System.ServiceModel.Description.MetadataExchangeClient> traite automatiquement les références, à votre place, dans des documents WSDL (Web Services Description Language), des schémas XML et des documents MEX. La taille de l'objet <xref:System.ServiceModel.Description.MetadataSet> créé à partir des métadonnées récupérées est directement proportionnelle à la valeur <xref:System.ServiceModel.Description.MetadataExchangeClient.MaximumResolvedReferences%2A> de l'instance <xref:System.ServiceModel.Description.MetadataExchangeClient> utilisée et à la valeur `MaxReceivedMessageSize` de la liaison utilisée par cette instance <xref:System.ServiceModel.Description.MetadataExchangeClient>. Affectez à ces quotas les valeurs appropriées définies par votre scénario.  
  
 Dans WCF, les métadonnées de service sont traitées en tant que XML. Lors du traitement de documents XML, les applications doivent se protéger contre des structures XML malveillantes. Utilisez <xref:System.Xml.XmlDictionaryReader> avec les quotas appropriés lors du traitement XML et affectez également la valeur <xref:System.Xml.XmlTextReader.DtdProcessing%2A> à la propriété <xref:System.Xml.DtdProcessing.Prohibit> .  
  
 Le système de métadonnées dans WCF est extensible et les extensions de métadonnées peuvent être inscrites dans votre fichier de configuration d’application (consultez [extension du système de métadonnées](../extending/extending-the-metadata-system.md)). Les extensions de métadonnées peuvent exécuter du code arbitraire, vous devez donc protéger le fichier de configuration de l'application avec des listes de contrôle d'accès (ACL) appropriées et inscrire uniquement les implémentations d'extensions de métadonnées approuvées.  
  
## <a name="validating-generated-clients"></a>Validation des clients générés  

 Lorsque vous générez du code client à partir de métadonnées récupérées d'une source non approuvée, validez le code client généré pour vous assurer que le client généré est conforme aux stratégies de sécurité des applications clientes. Vous pouvez utiliser un comportement de validation pour vérifier les paramètres sur votre liaison cliente ou inspecter visuellement le code généré par les outils. Pour obtenir un exemple d’implémentation d’un client qui valide des comportements, consultez [validation client](../samples/client-validation.md).  
  
## <a name="protecting-application-configuration-files"></a>Protection des fichiers de configuration d'application  

 Le fichier de configuration d'application d'un service peut spécifier si des métadonnées doivent être publiées et de quelle façon. Il est judicieux de protéger le fichier de configuration d'application à l'aide des listes de contrôle d'accès (ACL) appropriées pour vous assurer qu'aucun intrus ne pourra modifier ces paramètres.  
  
## <a name="see-also"></a>Voir aussi

- [Procédure : sécuriser des points de terminaison de métadonnées](how-to-secure-metadata-endpoints.md)
- [Sécurité](security.md)
