---
title: 'Comment : héberger un service WCF dans IIS'
description: Découvrez comment créer un service WCF hébergé dans Internet Information Services (IIS). Vous pouvez utiliser l'hébergement IIS uniquement avec un transport HTTP.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: 2ba0ae7adedc3bf0e0ca0cb92b4205edc968a5d8
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86052011"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a>Comment : héberger un service WCF dans IIS
Cette rubrique décrit les étapes de base requises pour créer un service Windows Communication Foundation (WCF) hébergé dans Internet Information Services (IIS). Dans cette rubrique, on suppose que vous connaissez IIS et que vous comprenez la manière d'utiliser l'outil d'administration IIS pour créer et gérer des applications IIS. Pour plus d’informations sur IIS, consultez [Internet Information Services](https://www.iis.net/). Un service WCF qui s’exécute dans l’environnement IIS tire pleinement parti des fonctionnalités d’IIS, telles que le recyclage de processus, l’arrêt inactif, le contrôle d’intégrité des processus et l’activation basée sur des messages. Cette option d'hébergement requiert que les services IIS soient configurés correctement, mais n'exige pas l'écriture d'un code d'hébergement dans le cadre de l'application. Vous pouvez utiliser l'hébergement IIS uniquement avec un transport HTTP.  
  
 Pour plus d’informations sur la façon dont WCF et ASP.NET interagissent, consultez [services WCF et ASP.net](wcf-services-and-aspnet.md). Pour plus d’informations sur la configuration de la sécurité, consultez [sécurité](security.md).  
  
 Pour obtenir la copie source de cet exemple, consultez [l’hébergement IIS à l’aide du code inline](../samples/iis-hosting-using-inline-code.md).  
  
### <a name="to-create-a-service-hosted-by-iis"></a>Pour créer un service hébergé par IIS  
  
1. Vérifiez que les services IIS sont installés et s'exécutent sur votre ordinateur. Pour plus d’informations sur l’installation et la configuration d’IIS, consultez [installation et configuration d’iis 7,0](https://docs.microsoft.com/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista)  
  
2. Créez un nouveau dossier pour vos fichiers d’application appelé « IISHostedCalcService », vérifiez que ASP.NET a accès au contenu du dossier et utilisez l’outil de gestion IIS pour créer une application IIS qui se trouve physiquement dans ce répertoire d’application. Lors de la création d'un alias pour le répertoire de l'application, utilisez « IISHostedCalc ».  
  
3. Créez un fichier appelé « service.svc » dans le répertoire de l'application. Modifiez ce fichier en ajoutant l' @ServiceHost élément suivant.  
  
   ```aspx-csharp
   <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>
   ```  
  
4. Créez un sous-répertoire App_Code dans le répertoire de l'application.  
  
5. Créez un fichier de code nommé Service.cs dans le sous-répertoire App_Code.  
  
6. Ajoutez les instructions using suivantes en tête du fichier Service.cs.  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7. Ajoutez la déclaration d'espace de noms suivante à la suite des instructions using.  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8. Définissez le contrat de service à l'intérieur de la déclaration d'espace de noms, tel qu'indiqué dans le code suivant.  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. Implémentez le contrat de service après la définition du contrat de service, tel qu'indiqué dans le code suivant.  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. Créez un fichier nommé « Web.config » dans le répertoire de l'application et ajoutez le code de configuration suivant dans le fichier. Lors de l’exécution, l’infrastructure WCF utilise les informations pour construire un point de terminaison avec lequel les applications clientes peuvent communiquer.  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]
  
     L'exemple spécifie explicitement les points de terminaison dans le fichier de configuration. Si vous n'ajoutez pas de points de terminaison au service, le runtime ajoute les points de terminaison par défaut. Pour plus d’informations sur les points de terminaison, les liaisons et les comportements par défaut, consultez [configuration simplifiée](../simplified-configuration.md) et [configuration simplifiée pour les services WCF](../samples/simplified-configuration-for-wcf-services.md).  
  
11. Pour vous assurer que le service est hébergé correctement, ouvrez une instance d'Internet Explorer et naviguez jusqu'à l'URL du service : `http://localhost/IISHostedCalc/Service.svc`  
  
## <a name="example"></a>Exemple  
 L'intégralité du code pour le service de calculatrice hébergé IIS est présentée ci-dessous.  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)]
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)]
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a>Voir aussi

- [Hébergement dans les services IIS (Internet Information Services)](hosting-in-internet-information-services.md)
- [Hébergement de services](../hosting-services.md)
- [Services WCF et ASP.NET](wcf-services-and-aspnet.md)
- [Sécurité](security.md)
- [Fonctionnalités d’hébergement de Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
