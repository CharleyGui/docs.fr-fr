---
title: UriTemplate Table, exemple
ms.date: 03/30/2017
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
ms.openlocfilehash: fb5932acce60e2da45f99730580237d31130d918
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715407"
---
# <a name="uritemplate-table-sample"></a>UriTemplate Table, exemple
La classe <xref:System.UriTemplateTable> fournit une structure de table associative de type dictionnaire permettant d'utiliser un ensemble d'instances d'`UriTemplate`. Les URI (Uniform Resource Identifier) spécifiques peuvent être mis en correspondance avec tous les modèles de la table de manière efficace, et les données associées au modèle mis en correspondance peuvent être récupérées.  
  
 Cet exemple présente les concepts clés suivants relatifs à la classe `UriTemplateTable` :  
  
- Syntaxe d'instanciation de `UriTemplateTable`.  
  
- Remplissage de `UriTemplateTable` avec un jeu de paires clé/valeur.  
  
- Mise en correspondance d'un URI candidat avec la table à l'aide de <xref:System.UriTemplateTable.MatchSingle%2A>.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Cet exemple se trouve dans le répertoire suivant.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a>Voir aussi

- [Répartiteur de table UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
- [UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
