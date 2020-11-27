---
title: Sécurité de transport HTTP
ms.date: 03/30/2017
ms.assetid: d3439262-c58e-4d30-9f2b-a160170582bb
ms.openlocfilehash: 1af9913ac977b0e1c112ca818a04842af9f1307c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280557"
---
# <a name="http-transport-security"></a>Sécurité de transport HTTP

Lors de l'utilisation du protocole HTTP comme transport, la sécurité est fournie par une implémentation SSL (Secure Sockets Layer). SSL est largement utilisé sur Internet pour authentifier un service auprès d'un client, puis pour fournir la confidentialité (chiffrement) au canal. Cette rubrique explique comment fonctionne le protocole SSL et comment il est implémenté dans Windows Communication Foundation (WCF).  
  
## <a name="basic-ssl"></a>Protocole SSL de base  

 On peut expliquer le fonctionnement du protocole SSL en prenant comme exemple un scénario typique, à savoir le site web d’une banque. Le site autorise un client à se connecter avec un nom d'utilisateur et un mot de passe. Après avoir été authentifié, l’utilisateur peut effectuer des transactions, par exemple afficher les soldes de ses comptes, régler des factures et transférer de l’argent d’un compte à un autre.  
  
 Lorsqu’un utilisateur visite pour la première fois le site, le mécanisme SSL commence une série de négociations, appelées « *négociation*», avec le client de l’utilisateur (dans ce cas, Internet Explorer). SSL authentifie tout d'abord le site de la banque auprès du client. Il s'agit d'une étape essentielle car les clients doivent d'abord s'assurer qu'ils communiquent avec le site réel, et non avec un site malveillant qui tente de les inciter à taper leur nom d'utilisateur et leur mot de passe. SSL effectue cette authentification en utilisant un certificat SSL fourni par une autorité approuvée, telle que VeriSign. La logique est la suivante : VeriSign se tient garant de l'identité du site de la banque. Étant donné qu'Internet Explorer approuve VeriSign, le site est approuvé. Si vous souhaitez contacter VeriSign, vous pouvez cliquer sur le logo VeriSign. Une déclaration d'authenticité s'affiche alors, avec la date d'expiration du certificat et l'entité à laquelle il a été délivré (le site de la banque).  
  
 Pour initier une session sécurisée, le client envoie l'équivalent d'un « bonjour » au serveur avec une liste d'algorithmes de chiffrement qu'il peut utiliser pour signer, générer des hachages et chiffrer et déchiffrer. En réponse, le site envoie un accusé de réception et son choix de l’une des suites d’algorithmes. Durant ce protocole de transfert initial, les deux correspondants envoient et reçoivent des valeurs à usage unique. Une valeur à usage *unique* est un élément de données généré de manière aléatoire, qui est utilisé conjointement avec la clé publique du site pour créer un hachage. Un *hachage* est un nouveau nombre qui est dérivé des deux nombres à l’aide d’un algorithme standard, tel que SHA1. (Le client et le site échangent également des messages pour s’accorder sur l’algorithme de hachage à utiliser.) Le hachage est unique et est utilisé uniquement pour la session entre le client et le site pour chiffrer et déchiffrer les messages. Le client et le service possèdent la valeur à usage unique d'origine et la clé publique du certificat ; ils peuvent donc tous deux générer le même hachage. Par conséquent, le client valide le hachage envoyé par le service en (a) utilisant l'algorithme convenu pour calculer le hachage à partir des données, et (b) en le comparant au hachage envoyé par le service ; si les deux correspondent, le client a l'assurance que le hachage n'a pas été falsifié. Le client peut ensuite utiliser ce hachage comme clé pour chiffrer un message qui contient un autre nouveau hachage. Le service peut déchiffrer le message à l'aide du hachage et récupérer cet avant-dernier hachage. Les informations accumulées (valeurs à usage unique, clé publique et autres données) sont maintenant connues des deux parties, et un hachage définitif (ou clé principale) peut être créé. Cette dernière clé est envoyée chiffrée à l'aide de l'avant-dernier hachage. La clé principale est ensuite utilisée pour chiffrer et déchiffrer les messages pour le reste de la session. Étant donné que le client et le service utilisent la même clé, on parle également de *clé de session*.  
  
 La clé de session se caractérise également par le fait qu'il s'agit d'une clé symétrique, ou d'un « secret partagé ». Le fait de disposer d’une clé symétrique est important car cela réduit le calcul requis par les deux côtés de la transaction. Si chaque message exigeait un nouvel échange de valeurs à usage unique et de hachages, les performances s'en trouveraient dégradées. Par conséquent, le but ultime du protocole SSL est d'utiliser une clé symétrique qui permet aux messages de circuler librement d'un côté à l'autre avec un niveau de sécurité et de rendement supérieur.  
  
 La description précédente est une version simplifiée de ce qui se produit, car le protocole peut varier d'un site à un autre. Il est également possible que le client et le site génèrent tous deux des valeurs à usage unique combinées de façon algorithmique durant le protocole de transfert, afin d'ajouter de la complexité, et par conséquent de la protection, au processus d'échange de données.  
  
### <a name="certificates-and-public-key-infrastructure"></a>Certificats et infrastructure à clé publique  

 Pendant le protocole de transfert, le service envoie également son certificat SSL au client. Le certificat contient des informations, telles que sa date d'expiration, l'autorité émettrice et l'URI (Uniform Resource Identifier) du site. Le client compare l'URI à celui qu'il a contacté initialement afin de s'assurer qu'ils correspondent, et il vérifie également la date et l'autorité émettrice.  
  
 Chaque certificat a deux clés : une clé privée et une clé publique, et les deux sont appelées *paire de clés d’échange*. En bref, la clé privée est connue uniquement du propriétaire du certificat, alors que la clé publique est lisible à partir du certificat. L’une ou l’autre clé peut être utilisée pour chiffrer ou déchiffrer un condensat, un hachage ou une autre clé, mais uniquement comme opérations contraires. Par exemple, si le client chiffre un message avec la clé publique, seul le site peut déchiffrer le message à l'aide de la clé privée. De même, si le site chiffre un message avec la clé privée, le client peut le déchiffrer avec la clé publique. Cela permet au client d'être certain que les messages sont échangés uniquement avec le propriétaire de la clé privée, car seuls les messages chiffrés avec la clé privée peuvent être déchiffrés avec la clé publique. Le site est assuré qu'il échange des messages avec un client qui a effectué le chiffrement à l'aide de la clé publique. Cet échange n'est cependant sécurisé que pour un protocole de transfert initial ; c'est pourquoi de nombreuses autres opérations sont exécutées afin de créer la clé symétrique. Néanmoins, toutes les communications dépendent du fait que le service possède un certificat SSL valide.  
  
## <a name="implementing-ssl-with-wcf"></a>Implémentation du protocole SSL avec WCF  

 La sécurité de transport HTTP (ou SSL) est fournie en externe à WCF. Vous pouvez implémenter SSL de deux manières ; le facteur décisif concerne le mode d'hébergement de votre application :  
  
- Si vous utilisez Internet Information Services (IIS) comme hôte WCF, utilisez l’infrastructure IIS pour configurer un service SSL.  
  
- Si vous créez une application WCF auto-hébergée, vous pouvez lier un certificat SSL à l’adresse à l’aide de l’outil HttpCfg.exe.  
  
### <a name="using-iis-for-transport-security"></a>Utilisation des services Internet (IIS) pour la sécurité de transport  
  
#### <a name="iis-70"></a>IIS 7.0  

 Pour configurer IIS 7,0 en tant qu’hôte sécurisé (à l’aide de SSL), consultez [configuration de protocole SSL dans IIS 7,0](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771438(v=ws.10)).  
  
Pour configurer des certificats à utiliser avec IIS 7,0, consultez [Configuration des certificats de serveur dans iis 7,0](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).  
  
#### <a name="iis-60"></a>IIS 6.0  

 Pour configurer IIS 6,0 en tant qu’hôte sécurisé (à l’aide de SSL), consultez [configuration de protocole SSL](/previous-versions/windows/it-pro/windows-server-2003/cc736992(v=ws.10)).  
  
 Pour configurer des certificats à utiliser avec IIS 6,0, consultez [Certificates_IIS_SP1_Ops](/previous-versions/windows/it-pro/windows-server-2003/cc757474(v=ws.10)).  
  
### <a name="using-httpcfg-for-ssl"></a>Utilisation de HttpCfg pour SSL  

 Si vous créez une application WCF auto-hébergée, utilisez l’outil [HttpCfg.exe](/windows/win32/http/httpcfg-exe) .
  
 Pour plus d’informations sur l’utilisation de l’outil HttpCfg.exe pour configurer un port avec un certificat X. 509, consultez [procédure : configurer un port avec un certificat SSL](how-to-configure-a-port-with-an-ssl-certificate.md).  
  
## <a name="see-also"></a>Voir aussi

- [Sécurité de transport](transport-security.md)
- [Sécurité des messages](message-security-in-wcf.md)
