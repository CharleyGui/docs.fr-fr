---
title: Sélection et validation de certificats
description: Découvrez les différentes façons dont les classes System.Net offrent pour sélectionner et valider des certificats pour les connexions SSL/TLS.
ms.date: 03/30/2017
ms.assetid: c933aca2-4cd0-4ff1-9df9-267143f25a6f
ms.openlocfilehash: a85b6947c20f7dbced1fb6ad6e79f3134ce1f57b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96287512"
---
# <a name="certificate-selection-and-validation"></a>Sélection et validation de certificats

Les classes <xref:System.Net> prennent en charge plusieurs manières de sélectionner et de valider <xref:System.Security.Cryptography.X509Certificates> pour les connexions SSL (Secure Socket Layer). Un client peut sélectionner un ou plusieurs certificats pour s’authentifier auprès d’un serveur. Un serveur peut exiger qu’un certificat client ait un ou plusieurs attributs spécifiques pour l’authentification.  
  
## <a name="definition"></a>Définition  

 Un certificat est un flux d’octets ASCII qui contient une clé publique, des attributs (tels que numéro de version, numéro de série et date d’expiration) et une signature numérique fournie par une autorité de certification. Les certificats servent à établir une connexion chiffrée ou à authentifier un client auprès d’un serveur.  
  
## <a name="client-certificate-selection-and-validation"></a>Sélection et validation de certificats clients  

 Un client peut sélectionner un ou plusieurs certificats pour une connexion SSL spécifique. Les certificats clients peuvent être associés à la connexion SSL à un serveur web ou à un serveur de messagerie SMTP. Un client ajoute des certificats à une collection d’objets de classe <xref:System.Security.Cryptography.X509Certificates.X509Certificate> ou <xref:System.Security.Cryptography.X509Certificates.X509Certificate2>. Si l’on prend la messagerie électronique comme exemple, la collection de certificats est une instance d’un <xref:System.Security.Cryptography.X509Certificates.X509CertificateCollection> associée à la propriété <xref:System.Net.Mail.SmtpClient.ClientCertificates%2A> de la classe <xref:System.Net.Mail.SmtpClient>. La classe <xref:System.Net.HttpWebRequest> a une propriété <xref:System.Net.HttpWebRequest.ClientCertificates%2A> similaire.  
  
 La principale différence entre les classes <xref:System.Security.Cryptography.X509Certificates.X509Certificate> et <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> est que la clé privée doit résider dans le magasin de certificats pour la classe <xref:System.Security.Cryptography.X509Certificates.X509Certificate>.  
  
 Même si des certificats sont ajoutés à une collection et associés à une connexion SSL spécifique, aucun certificat ne sera envoyé au serveur si celui-ci ne le demande pas. Si plusieurs certificats clients sont définis sur une connexion, le meilleur sera utilisé sur la base d’un algorithme qui prend en compte la correspondance entre les émetteurs de certificats figurant sur la liste fournie par le serveur et le nom de l’émetteur du certificat client.  
  
 La classe <xref:System.Net.Security.SslStream> fournit un contrôle accru sur la négociation SSL. Un client peut spécifier un délégué pour sélectionner le certificat client à utiliser.  
  
 Un serveur distant peut vérifier qu’un certificat client est valide, à jour et signé par l’autorité de certification appropriée. Un délégué peut être ajouté à <xref:System.Net.ServicePointManager.ServerCertificateValidationCallback%2A> pour appliquer la validation de certificat.  
  
## <a name="client-certificate-selection"></a>Sélection du certificat client  

 Le .NET Framework sélectionne le certificat client à présenter au serveur de la manière suivante :  
  
1. Si un certificat client a été présenté précédemment au serveur, le certificat est mis en cache lors de la première présentation puis réutilisé lors des requêtes de certificats clients ultérieures.  
  
2. Si un délégué est présent, utilisez toujours le résultat du délégué comme certificat client à sélectionner. Essayez d’utiliser un certificat mis en cache dans la mesure du possible, mais n’utilisez pas d’informations d’identification anonymes mises en cache si le délégué a retourné la valeur null et que la collection de certificats n’est pas vide.  
  
3. S’il s’agit de la première demande de certificat client, le Framework énumère les certificats dans <xref:System.Security.Cryptography.X509Certificates.X509Certificate> ou les objets de classe <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> associés à la connexion, à la recherche d’une correspondance entre les émetteurs de certificats figurant sur la liste fournie par le serveur et le nom de l’émetteur du certificat client. Le premier certificat qui correspond est envoyé au serveur. Si aucun certificat ne correspond ou si la collection de certificats est vide, des informations d’identification anonymes sont envoyées au serveur.  
  
## <a name="tools-for-certificate-configuration"></a>Outils pour la configuration de certificat  

 Un certain nombre d’outils sont disponibles pour la configuration des certificats clients et de serveur.  
  
 Vous pouvez utiliser *Winhttpcertcfg.exe* pour configurer les certificats clients. L’outil *Winhttpcertcfg.exe* est fourni avec le SDK Windows Server 2003. Cet outil est également disponible en téléchargement dans le cadre des outils du Kits de ressources techniques Windows Server 2003 sur [www.microsoft.com](https://www.microsoft.com).  
  
Vous pouvez utiliser *HttpCfg.exe* pour configurer des certificats de serveur pour la classe <xref:System.Net.HttpListener>. *HttpCfg.exe* est l’un des outils de support pour Windows Server 2003 et Windows XP Service Pack 2. *HttpCfg.exe* et les autres outils de support ne sont pas installés par défaut sur Windows Server 2003 ou Windows XP. Sur Windows Server 2003, les outils de support sont installés séparément à partir du dossier et du fichier suivants sur le CD-ROM de Windows Server 2003 :  
  
 \Support\Tools\Suptools.msi  
  
 Pour une utilisation avec Windows XP Service Pack 2, les Outils de support Windows XP sont disponibles en téléchargement sur [www.microsoft.com](https://www.microsoft.com).  
  
 Le code source d’une version de l’outil *HttpCfg.exe* est également fourni en guise d’exemple avec le SDK Windows Server. Le code source de l’exemple *HttpCfg.exe* est installé par défaut avec les exemples de mise en réseau dans le cadre du SDK Windows sous le dossier suivant :  
  
 *C:\Program Files\Microsoft SDKs\Windows\v1.0\Samples\NetDS\http\serviceconfig*  
  
 Outre ces outils, les classes <xref:System.Security.Cryptography.X509Certificates.X509Certificate> et <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> fournissent des méthodes pour charger un certificat à partir du système de fichiers.  
  
## <a name="see-also"></a>Voir aussi

- [Sécurité dans la programmation réseau](security-in-network-programming.md)
- [Programmation réseau dans le .NET Framework](index.md)
