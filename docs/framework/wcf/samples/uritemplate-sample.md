---
title: UriTemplate, exemple
ms.date: 03/30/2017
ms.assetid: 0aaf91d0-ce18-468d-8006-bc9bc2e48231
ms.openlocfilehash: 15799c1aaf3ed7df5f7721368dea426665dcf335
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044597"
---
# <a name="uritemplate-sample"></a>UriTemplate, exemple
La classe <xref:System.UriTemplate> fournit des méthodes pour utiliser des ensembles d'URI qui partagent une structure commune. Cet exemple illustre les concepts clés suivants relatifs au `UriTemplate` :  
  
- Syntaxe de création des modèles.  
  
- Instanciation d'URI depuis un `UriTemplate` à l'aide de <xref:System.UriTemplate.BindByName%2A> et <xref:System.UriTemplate.BindByPosition%2A>.  
  
- <xref:System.UriTemplateTable.Match%2A>, qui est l'opération inverse de `BindByName` et `BindByPosition`.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et. Cet exemple se trouve dans le répertoire suivant.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplate`  
  
## <a name="see-also"></a>Voir aussi

- [Table UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [Répartiteur de table UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
