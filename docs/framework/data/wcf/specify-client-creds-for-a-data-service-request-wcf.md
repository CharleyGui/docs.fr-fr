---
title: "Procédure : spécifier les informations d'identification du client pour une demande de service de données (WCF Data Services)"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 1632f9af-e45f-4363-9222-03823daa8e28
ms.openlocfilehash: fd69d5f7eddf713612000b0ad677e7ada378553e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91180658"
---
# <a name="how-to-specify-client-credentials-for-a-data-service-request-wcf-data-services"></a>Procédure : spécifier les informations d'identification du client pour une demande de service de données (WCF Data Services)

Par défaut, la bibliothèque cliente ne fournit pas d’informations d’identification lors de l’envoi d’une demande à un service OData. Toutefois, vous pouvez spécifier que les informations d'identification soient transmises aux demandes authentifiées sur le service de données en fournissant un <xref:System.Net.NetworkCredential> pour la propriété <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> du <xref:System.Data.Services.Client.DataServiceContext>. Pour plus d'informations, consultez [Securing WCF Data Services](securing-wcf-data-services.md). L’exemple de cette rubrique montre comment fournir explicitement des informations d’identification utilisées par le client WCF Data Services lors de la demande de données à partir du service de données.  
  
 L'exemple dans cette rubrique utilise l'exemple de service de données Northwind et des classes de service de données clientes générées automatiquement. Ce service et les classes de données clientes sont créés lorsque vous terminez le [démarrage rapide WCF Data Services](quickstart-wcf-data-services.md). Vous pouvez également utiliser l' [exemple de service de données Northwind](https://services.odata.org/Northwind/Northwind.svc/) publié sur le site Web OData. Cet exemple de service de données est en lecture seule et toute tentative d’enregistrement des modifications retourne une erreur. Les exemples de services de données sur le site Web OData autorisent l’authentification anonyme.  
  
## <a name="example"></a>Exemple  

 L'exemple suivant provient de la page code-behind d'un fichier XAML (Extensible Application Markup Language) qui est la page principale de l'application Windows Presentation Framework. Cet exemple affiche une instance `LoginWindow` pour collecter les informations d'authentification de l'utilisateur, puis les utilise pour la création d'une demande au service de données.  
  
 [!code-csharp[Astoria Northwind Client#ClientCredentials](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/clientcredentials.xaml.cs#clientcredentials)]  
 [!code-vb[Astoria Northwind Client#ClientCredentials](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/clientcredentials.xaml.vb#clientcredentials)]
  
## <a name="example"></a>Exemple  

 Vous trouverez ci-après le code XAML qui définit la page principale de l'application WPF.  
  
 [!code-xaml[Astoria Northwind Client#ClientCredentialsXaml](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/clientcredentials.xaml#clientcredentialsxaml)]  
  
## <a name="example"></a>Exemple  

 L'exemple suivant provient de la page code-behind de la fenêtre utilisée pour collecter les informations d'authentification de l'utilisateur avant une demande au service de données.  
  
 [!code-csharp[Astoria Northwind Client#ClientCredentialsLogin](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/clientcredentialslogin.xaml.cs#clientcredentialslogin)]  
 [!code-vb[Astoria Northwind Client#ClientCredentialsLogin](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/clientcredentialslogin.xaml.vb#clientcredentialslogin)]
  
## <a name="example"></a>Exemple  

 Vous trouverez ci-après le code XAML qui définit la connexion de l'application WPF.  
  
 [!code-xaml[Astoria Northwind Client#ClientCredentialsLoginXaml](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/clientcredentialslogin.xaml#clientcredentialsloginxaml)]  
  
## <a name="net-framework-security"></a>Sécurité du .NET Framework  

 Les considérations sur la sécurité suivantes s'appliquent à l'exemple de cette rubrique :  
  
- Pour vérifier que les informations d'identification fournies dans cet exemple fonctionnent, le service de données Northwind doit utiliser un schéma d'authentification autre que l'accès anonyme. Autrement, le site web qui héberge le service de données ne demandera aucune information d’identification.  
  
- Les informations d'identification de l'utilisateur ne doivent être demandées que pendant l'exécution et ne doivent pas être mises en cache. Les informations d'identification doivent toujours être stockées de manière sécurisée.  
  
- Les données transmises avec une authentification de base et Digest ne sont pas chiffrées, par conséquent les données sont visibles par tous. De plus, les informations d'authentification de base (nom d'utilisateur et mot de passe) sont envoyées en texte clair et peuvent être interceptées.  
  
 Pour plus d'informations, consultez [Securing WCF Data Services](securing-wcf-data-services.md).  
  
## <a name="see-also"></a>Voir aussi

- [Sécurisation de WCF Data Services](securing-wcf-data-services.md)
- [Bibliothèque client services de données WCF](wcf-data-services-client-library.md)
