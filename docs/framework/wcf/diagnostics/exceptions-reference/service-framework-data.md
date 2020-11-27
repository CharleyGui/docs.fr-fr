---
title: Données d'infrastructure de service
ms.date: 03/30/2017
ms.assetid: 2a2c8ddc-4e82-4e7f-a79f-97085c469517
ms.openlocfilehash: 8bb6e9df6a77eda5875981a0bf7783f50671a589
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255778"
---
# <a name="service-framework-data"></a>Données d'infrastructure de service

Cette rubrique répertorie toutes les exceptions générées par les données d'infrastructure de service.  
  
## <a name="exception-list"></a>Liste des exceptions  
  
|Code de la ressource|Chaîne de la ressource|  
|-------------------|---------------------|  
|AddressingExtensionInBadNS|L'élément spécifié dans l'espace de noms indiqué n'est pas valide. Cela signifie que l’élément spécifié est un élément en double ou que l’extension n’est pas légale parce que les éléments d’extension ne peuvent pas être dans l’espace de noms d’adressage.|  
|BinaryEncoderSessionInvalid|La session de l'encodeur binaire n'est pas valide en raison d'une erreur lors du décodage d'un message précédent.|  
|CannotDetectAddressingVersion|Impossible de détecter la version de WS-Addressing. EndpointAddress ne commence pas par un élément.|  
|CouldNotFindNamespaceForPrefix|Le préfixe spécifié n'a aucune liaison d'espace de noms dans la portée.|  
|EncoderBadContentType|Impossible de traiter dans contentType.|  
|EncoderEnvelopeVersionMismatch|La version d'enveloppe du message entrant spécifié ne correspond pas à l'encodeur spécifié. Assurez-vous que la liaison est configurée avec la même version que les messages attendus.|  
|EncoderMessageVersionMismatch|La version du message sortant spécifié ne correspond pas à l'encodeur spécifié. Assurez-vous que la liaison est configurée avec la même version que le message.|  
|ExtraContentIsPresentInFaultDetail|Du contenu XML (Extensible Markup Language) supplémentaire est présent dans l'élément de détail d'erreur. Un seul élément est autorisé.|  
|FilterBadTableType|L'élément IMessageFilterTable créé pour un filtre ne peut pas être un élément MessageFilterTable ou être dérivé de MessageFilterTable.|  
|FilterTableInvalidForLookup|MessageFilterTable est endommagé. La recherche demandée ne peut pas être effectuée.|  
|MandatoryHeaderNotUnderstood|Un ou plusieurs blocs d'en-tête SOAP (Simple Object Access Protocol) requis n'ont pas été compris.|  
|MessageBodyIsStream|Le corps du message est un flux.|  
|MessageBodyIsUnknown|Le format du corps du message est inconnu.|  
|MessageBodyReaderInvalidReadState|L'état ReadState spécifié du lecteur de corps du message ne peut pas être consommé.|  
|MessageTextEncodingNotSupported|L'encodage de texte spécifié qui est utilisé dans le format du message texte n'est pas pris en charge.|  
|MissingMessageID|Un en-tête MessageID est manquant dans un message de demande. Un en-tête MessageID est requis pour corréler une réponse.|  
|MultipleMessageHeaders|Plusieurs en-têtes avec le nom et l'espace de noms spécifiés ont été trouvés.|  
|MultipleMessageHeadersWithActor|Plusieurs en-têtes avec le nom, l'espace de noms et le rôle spécifiés ont été trouvés.|  
|MultipleRelatesToHeaders|Plusieurs en-têtes RelatesTo avec la relation spécifiée ont été trouvés. Un seul en-tête est autorisé par relation.|  
|QueryFunctionTypeNotSupported|Le type de retour spécifié pour IXsltContextFunction n’est pas pris en charge.|  
|QueryIteratorOutOfScope|XPathNodeIterator a été invalidé. Les éléments XPathNodeIterator passés comme arguments à des fonctions IXsltContextFunctions sont uniquement valides à l'intérieur de la fonction. Ils ne peuvent pas être mis en cache pour une utilisation ultérieure ou être retournés par la fonction.|  
|QueryVariableNull|Les méthodes IXsltContextVariable ne peuvent pas retourner la valeur null.|  
|QueryVariableTypeNotSupported|Le type dérivé IXsltContextVariable spécifié n'est pas pris en charge.|  
|ReceiveShutdownReturnedMessage|Le canal a reçu un message d'entrée inattendu avec l'action spécifiée lors de la fermeture. Fermez le canal lorsque vous n'attendez plus de message d'entrée.|  
|XmlBufferInInvalidState|Une erreur interne s'est produite. L'opération ne peut pas être exécutée à cause de l'état de la mémoire tampon XML.|  
|XmlBufferQuotaExceeded|La taille nécessaire à la mise en mémoire tampon du contenu XML a dépassé le quota de mémoire tampon.|
