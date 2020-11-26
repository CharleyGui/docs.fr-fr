---
title: 'Procédure : importer des assertions de stratégie personnalisées'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f41d787-accb-4a10-bfc6-a807671d1581
ms.openlocfilehash: fb5e3ba5faca1b32eef63ac174bcd7731ee50771
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249148"
---
# <a name="how-to-import-custom-policy-assertions"></a>Procédure : importer des assertions de stratégie personnalisées

Les assertions de stratégie décrivent les fonctions et les exigences d’un point de terminaison de service.  Les applications clientes peuvent utiliser des assertions de stratégie dans les métadonnées de service pour configurer la liaison cliente ou personnaliser le contrat de service d’un point de terminaison de service.  
  
 Les assertions de stratégie personnalisées sont importées en implémentant l'interface <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> et en passant cet objet au système de métadonnées ou en enregistrant le type d'implémentation dans le fichier de configuration de votre application.  Les implémentations de l' <xref:System.ServiceModel.Description.IPolicyImportExtension> interface doivent fournir un constructeur sans paramètre.  
  
### <a name="to-import-custom-policy-assertions"></a>Pour importer des assertions de stratégie personnalisées  
  
1. Implémentez l'interface <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=nameWithType> sur une classe. Reportez-vous aux procédures ci-dessous.  
  
2. Insérez l'importateur de stratégie personnalisé selon l'une des méthodes suivantes :  
  
3. Utilisation d'un fichier de configuration. Reportez-vous aux procédures ci-dessous.  
  
4. Utilisation d’un fichier de configuration avec l' [outil utilitaire de métadonnées ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md). Reportez-vous aux procédures ci-dessous.  
  
5. Insertion par programme de l'importateur de stratégie. Reportez-vous aux procédures ci-dessous.  
  
### <a name="to-implement-the-systemservicemodeldescriptionipolicyimportextension-interface-on-any-class"></a>Pour implémenter l'interface System.ServiceModel.Description.IPolicyImportExtension sur une classe  
  
1. Dans la méthode <xref:System.ServiceModel.Description.IPolicyImportExtension.ImportPolicy%2A?displayProperty=nameWithType>, recherchez, pour chaque sujet de stratégie qui vous intéresse, les assertions de stratégie que vous souhaitez importer en appelant la méthode appropriée (selon sur la portée de l'assertion de votre choix) sur l'objet <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=nameWithType> passé à la méthode. L’exemple de code suivant indique comment utiliser la méthode <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> pour localiser l’assertion de stratégie personnalisée et la supprimer de la collection en une étape. Si vous utilisez la méthode de suppression pour localiser et supprimer l'assertion, l'étape 4 n'est pas nécessaire.  
  
     [!code-csharp[CustomPolicySample#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyimporter.cs#9)]
     [!code-vb[CustomPolicySample#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyimporter.vb#9)]  
  
2. Traitez les assertions de stratégie. Notez que le système de stratégie ne normalise pas les stratégies imbriquées et `wsp:optional`. Vous devez traiter ces constructions dans votre implémentation d'extension d'importation de stratégie.  
  
3. Exécutez la personnalisation sur la liaison ou le contrat qui prend en charge la fonction ou la spécification spécifiée par l’assertion de stratégie. En général, les assertions indiquent qu’une liaison requiert une configuration particulière ou un élément de liaison spécifique. Apportez ces modifications en accédant à la propriété <xref:System.ServiceModel.Description.PolicyConversionContext.BindingElements%2A?displayProperty=nameWithType>. D'autres assertions requièrent la modification du contrat.  Vous pouvez accéder et modifier le contrat à l'aide de la propriété <xref:System.ServiceModel.Description.PolicyConversionContext.Contract%2A?displayProperty=nameWithType>.  Notez que votre importateur de stratégie peut être appelé plusieurs fois pour la même liaison et le même contrat, mais pour des alternatives de stratégie différentes en cas d’échec de l’importation d’une alternative de stratégie. Votre code doit être résilient à ce comportement.  
  
4. Supprimez l'assertion de stratégie personnalisée de la collection d'assertions. Si vous ne supprimez pas l’assertion Windows Communication Foundation (WCF) suppose que l’importation de stratégie a échoué et n’importe pas la liaison associée. Si vous avez utilisé la méthode <xref:System.ServiceModel.Description.PolicyAssertionCollection.Remove%2A?displayProperty=nameWithType> pour localiser l’assertion de stratégie personnalisée et la supprimer de la collection en une étape, cette étape n’est pas nécessaire.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-a-configuration-file"></a>Pour insérer l'importateur de stratégie personnalisé dans le système de métadonnées à l'aide d'un fichier de configuration  
  
1. Ajoutez le type d’importateur à l’élément à l' `<extensions>` intérieur [\<policyImporters>](../../configure-apps/file-schema/wcf/policyimporters.md) de l’élément dans le fichier de configuration client.  
  
     [!code-xml[CustomPolicySample#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.exe.config#7)]
  
2. Dans l'application cliente, utilisez <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType> pour résoudre les métadonnées, l'importateur étant appelé automatiquement.  
  
     [!code-csharp[CustomPolicySample#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/client.cs#10)]
     [!code-vb[CustomPolicySample#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/client.vb#10)]  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-using-svcutilexe"></a>Pour insérer l'importateur de stratégie personnalisé dans le système de métadonnées à l'aide de Svcutil.exe  
  
1. Ajoutez le type d’importateur à l’élément à l' `<extensions>` intérieur [\<policyImporters>](../../configure-apps/file-schema/wcf/policyimporters.md) de l’élément dans le fichier de configuration Svcutil.exe.config. Vous pouvez également pointer Svcutil.exe pour charger les types d'importateur de stratégie enregistrés dans un autre fichier de configuration à l'aide de l'option `/svcutilConfig`.  
  
2. Utilisez l' [outil utilitaire de métadonnées ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) pour importer les métadonnées et l’importateur est appelé automatiquement.  
  
### <a name="to-insert-the-custom-policy-importer-into-the-metadata-system-programmatically"></a>Pour insérer par programme l'importateur de stratégie personnalisé dans le système de métadonnées  
  
1. Ajoutez l'importateur à la propriété <xref:System.ServiceModel.Description.MetadataImporter.PolicyImportExtensions%2A?displayProperty=nameWithType> (par exemple, si vous utilisez <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>) avant d'importer les métadonnées.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.WsdlImporter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType>
- [Extension du système de métadonnées](extending-the-metadata-system.md)
