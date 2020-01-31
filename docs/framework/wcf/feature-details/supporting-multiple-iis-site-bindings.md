---
title: Prise en charge de plusieurs liaisons de site IIS
ms.date: 03/30/2017
ms.assetid: 40440495-254d-45c8-a8c6-b29f364892ba
ms.openlocfilehash: e364be55687323d3059c4a7e084818e3f7d54d5f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743446"
---
# <a name="supporting-multiple-iis-site-bindings"></a>Prise en charge de plusieurs liaisons de site IIS
Lorsque vous hébergez un service Windows Communication Foundation (WCF) sous Internet Information Services (IIS) 7,0, vous souhaiterez peut-être fournir plusieurs adresses de base qui utilisent le même protocole sur le même site. Cela permet au même service de répondre à plusieurs URI différents. Cela est utile lorsque vous souhaitez héberger un service qui écoute sur `http://www.contoso.com` et `http://contoso.com`. Il est également utile de créer un service qui a une adresse de base pour les utilisateurs internes et une autre adresse de base pour les utilisateurs externes. Par exemple : `http://internal.contoso.com` et `http://www.contoso.com`.  
  
> [!NOTE]
> Ces fonctionnalités ne sont disponibles qu'en utilisant le protocole HTTP.  
  
## <a name="multiple-base-addresses"></a>Plusieurs adresses de base  
 Cette fonctionnalité est disponible uniquement pour les services WCF hébergés sous IIS. Cette option n'est pas activée par défaut. Pour l’activer, vous devez ajouter l’attribut `multipleSiteBindingsEnabled` au <`serviceHostingEnvironment`élément > dans votre fichier Web. config et lui affecter la valeur `true`, comme illustré dans l’exemple suivant.  
  
```xml  
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"/>  
```  
  
 Lors de l’hébergement d’un service WCF sous IIS, IIS crée une adresse de base pour vous en fonction de l’URI du répertoire virtuel qui contient l’application. Vous pouvez ajouter des adresses de base supplémentaires utilisant le même protocole, à l’aide du gestionnaire des services IIS pour ajouter une ou plusieurs liaisons à votre site web. Pour chaque liaison, spécifiez un protocole (HTTP ou HTTPS), une adresse IP, un port et un nom d’hôte. Pour plus d’informations sur l’utilisation de Internet Information Services Manager, voir [Gestionnaire des services Internet (IIS 7)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753842(v=ws.10)). Pour plus d’informations sur l’ajout de liaisons à un site, consultez [créer un site Web (IIS 7)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772350(v=ws.10)) .  
  
 La spécification de plusieurs adresses de base pour le même site affecte le contenu de la page d’aide WCF, l’importation du schéma et les informations WSDL/MEX générées par le service. La page d’aide de WCF affiche la ligne de commande à utiliser pour générer un client WCF qui peut communiquer avec le service. Cette ligne de commande contient uniquement la première adresse spécifiée dans la liaison IIS pour le site web. De même, lors de l’importation du schéma, seule la première adresse de base spécifiée dans la liaison IIS est utilisée. Les données WSDL et MEX contiennent toutes les adresses de base spécifiées dans les liaisons IIS.  
  
> [!WARNING]
> Cela signifie que si un service possède deux adresses de base, une pour les utilisateurs internes et l'autre pour les utilisateurs externes, les deux sont spécifiées dans les informations WSDL/MEX générées par le service.
