---
title: 'Comment : créer une application Framework de présentation Windows asynchrone (services de données WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, asynchronous operations
ms.assetid: 834614df-1427-4839-b0be-90f68e5afffd
ms.openlocfilehash: 67f6e27e4042e1cddbef8b99a2235e1a21d270d2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91152740"
---
# <a name="how-to-create-an-asynchronous-windows-presentation-framework-application-wcf-data-services"></a>Comment : créer une application Framework de présentation Windows asynchrone (services de données WCF)

Avec WCF Data Services, vous pouvez lier des données obtenues à partir d’un service de données à l’élément d’interface utilisateur d’une application WPF (Windows Presentation Framework). Pour plus d’informations, consultez [liaison de données à des contrôles](binding-data-to-controls-wcf-data-services.md). Vous pouvez également exécuter des opérations sur le service de données de manière asynchrone, ce qui permet à l’application de continuer à répondre en attendant une réponse à une demande de service de données. Les applications pour Silverlight sont obligatoires pour accéder de façon asynchrone au service de données. Pour plus d’informations, consultez [opérations asynchrones](asynchronous-operations-wcf-data-services.md).  
  
 Cette rubrique montre comment accéder de façon asynchrone à un service de données et lier les résultats aux éléments d'une application WPF. Les exemples dans cette rubrique utilisent l'exemple de service de données Northwind et des classes de service de données client générées automatiquement. Ce service et les classes de données clientes sont créés lorsque vous terminez le [démarrage rapide WCF Data Services](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemple  

 Vous trouverez ci-après le code XAML qui définit la fenêtre de l'application WPF.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingAsyncXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerordersasync.xaml#wpfdatabindingasyncxaml)]  
  
## <a name="example"></a>Exemple  

 La page code-behind suivante du fichier XAML exécute une requête asynchrone à l'aide du service de données et lie les résultats aux éléments dans la fenêtre WPF.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerordersasync.xaml.cs#wpfdatabindingasync)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerordersasync.xaml.vb#wpfdatabindingasync)]  
  
## <a name="see-also"></a>Voir aussi

- [Bibliothèque client services de données WCF](wcf-data-services-client-library.md)
