---
title: Combinaison de protocoles d'approbation dans les scénarios fédérés
ms.date: 03/30/2017
ms.assetid: d7b5fee9-2246-4b09-b8d7-9e63cb817279
ms.openlocfilehash: 5ce178c0b2c83469a26993ce6db2d6c87815543b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248173"
---
# <a name="mixing-trust-protocols-in-federated-scenarios"></a>Combinaison de protocoles d'approbation dans les scénarios fédérés

Il peut exister des scénarios où des clients fédérés communiquent avec un WSDL de service et un service de jeton de sécurité (STS) qui n'ont pas la même version d'approbation. Le WSDL de service peut contenir une assertion `RequestSecurityTokenTemplate` avec les éléments WS-Trust qui sont de versions différentes par rapport à STS. Dans ce cas, un client Windows Communication Foundation (WCF) convertit les éléments WS-Trust reçus à partir de `RequestSecurityTokenTemplate` pour qu’ils correspondent à la version d’approbation STS. WCF gère les versions d’approbation qui ne correspondent pas uniquement pour les liaisons standard. Tous les paramètres d’algorithme standard reconnus par WCF font partie de la liaison standard. Cette rubrique décrit le comportement WCF avec différents paramètres d’approbation entre le service et le STS.  
  
## <a name="rp-feb-2005-and-sts-feb-2005"></a>RP février 2005 et STS février 2005  

 Le WSDL pour la partie de confiance (RP) contient les éléments suivants dans la section `RequestSecurityTokenTemplate` :  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
 Le fichier de configuration client contient une liste de paramètres.  
  
 WCF ne peut pas faire la différence entre les paramètres du client et du service. Elle ajoute tous les paramètres et les envoie dans le `RequestSecurityTokenTemplate` (RST).  
  
## <a name="rp-trust-13-and-sts-trust-13"></a>Version d'approbation RP 1.3 et Version d'approbation STS 1.3  

 Le WSDL pour la partie de confiance (RP) contient les éléments suivants dans la section `RequestSecurityTokenTemplate` :  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
- `KeyWrapAlgorithm`  
  
 Le fichier de configuration client contient un élément `secondaryParameters` qui encapsule les paramètres spécifié par la partie de confiance.  
  
 WCF supprime les `EncryptionAlgorithm` `CanonicalizationAlgorithm` éléments, et `KeyWrapAlgorithm` de l’élément de niveau supérieur sous le RST si ceux-ci sont présents à l’intérieur de l' `SecondaryParameters` élément. WCF ajoute l' `SecondaryParameters` élément à l’RST sortant non modifié.  
  
## <a name="rp-trust-feb-2005-and-sts-trust-13"></a>Version d'approbation RP février 2005 et Version d'approbation STS 1.3  

 Le WSDL pour la partie de confiance (RP) contient les éléments suivants dans la section `RequestSecurityTokenTemplate` :  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
 Le fichier de configuration client contient une liste de paramètres.  
  
 À partir du fichier de configuration client, WCF ne peut pas faire la différence entre les paramètres du service et du client. Par conséquent, WCF convertit tous les paramètres en un espace de noms Trust version 1,3.  
  
 WCF gère les `KeyType` `KeySize` éléments, et `TokenType` comme suit :  
  
- Téléchargez le WSDL, créez la liaison et assignez `KeyType`, `KeySize` et `TokenType` à partir des paramètres RP. Le fichier de configuration client est alors généré.  
  
- Le client peut maintenant modifier tout paramètre dans le fichier de configuration.  
  
- Pendant l’exécution, WCF copie tous les paramètres spécifiés dans la `AdditionalTokenParameters` section du fichier de configuration client, à l’exception de `KeyType` , `KeySize` et `TokenType` , car ces paramètres sont comptabilisés pendant la génération du fichier de configuration.  
  
## <a name="rp-trust-13-and-sts-trust-feb-2005"></a>Version d'approbation RP 1.3 et Version d'approbation STS février 2005  

 Le WSDL pour la partie de confiance (RP) contient les éléments suivants dans la section `RequestSecurityTokenTemplate` :  
  
- `CanonicalizationAlgorithm`  
  
- `EncryptionAlgorithm`  
  
- `EncryptWith`  
  
- `SignWith`  
  
- `KeySize`  
  
- `KeyType`  
  
- `KeyWrapAlgorithm`  
  
 Le fichier de configuration client contient un élément `secondaryParamters` qui encapsule les paramètres spécifié par la partie de confiance.  
  
 WCF copie tous les paramètres spécifiés dans la `SecondaryParameters` section dans l’élément RST de niveau supérieur, mais ne les convertit pas en espace de noms 2005 WS-Trust.
