---
title: 'Comment : spécifier une liaison de client dans la configuration'
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: 574f56173c2acfcf41a5e9a9e99abe45281e3636
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184037"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a>Comment : spécifier une liaison de client dans la configuration
Dans cet exemple, une application console cliente est créée pour utiliser un service de calculatrice, et la liaison pour ce client est spécifiée de façon déclarative dans la configuration. Le client accède au service `CalculatorService`, lequel implémente l'interface `ICalculator`. Le service et le client utilisent la classe <xref:System.ServiceModel.BasicHttpBinding>.  
  
 La procédure présentée suppose que le service de calculatrice est en cours d'exécution. Pour plus d’informations sur la façon de construire le service, voir [comment : Spécifier une liaison de service dans la configuration](how-to-specify-a-service-binding-in-configuration.md). Il utilise également [l’outil utilitaire De métadonnées de servicemodel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) que Windows Communication Foundation (WCF) fournit pour générer automatiquement les composants du client. L'outil génère le code client et la configuration permettant d'accéder au service.  
  
 La construction du client se divise en deux parties. L'outil Svcutil.exe génère la calculatrice `ClientCalculator` qui implémente l'interface `ICalculator`. Cette application cliente est ensuite construite à l'aide d'une instance de `ClientCalculator`.  
  
 Il est généralement conseillé de spécifier de façon déclarative les informations de liaison et d'adresse dans la configuration plutôt que de manière impérative dans le code. La définition de points de terminaison dans le code est généralement peu pratique car les liaisons et les adresses pour un service déployé sont en général différentes de celles utilisées au cours du développement du service. Plus généralement, le fait de laisser les informations de liaison et d’adresse hors du code leur permet de changer sans nécessiter de recompilation ou de redéploiement de l’application.  
  
 Vous pouvez effectuer toutes les étapes de configuration suivantes en utilisant [l’outil d’éditeur de configuration (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Pour la copie source de cet exemple, voir l’échantillon [BasicBinding.](./samples/basicbinding.md)  
  
### <a name="specifying-a-client-binding-in-configuration"></a>Spécification d’une liaison de client dans la configuration  
  
1. Utilisez l'outil Svcutil.exe depuis la ligne de commande pour générer le code à partir des métadonnées de service.  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. Le client généré contient l'interface `ICalculator` qui définit le contrat de service auquel l'implémentation du client doit satisfaire.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. Le client généré contient également l'implémentation de `ClientCalculator`.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. Svcutil.exe génère également la configuration du client qui utilise la classe <xref:System.ServiceModel.BasicHttpBinding>. Lorsque vous utilisez Visual Studio, nommez ce fichier App.config. Notez que l’adresse et les informations contraignantes ne sont spécifiées nulle part à l’intérieur de la mise en œuvre du service. Par ailleurs, il n'est pas nécessaire d'écrire du code pour récupérer ces informations à partir du fichier de configuration.  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]

5. Créez une instance de `ClientCalculator` dans une application, puis appelez les opérations de service.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. Compilez, puis exécutez le client.  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation de liaisons pour configurer des services et des clients](using-bindings-to-configure-services-and-clients.md)
