---
title: 'Comment : spécifier une liaison de service dans la configuration'
description: Découvrez comment configurer un point de terminaison pour un service WCF dans un fichier de configuration. Un contrat est défini pour un service et implémenté dans une classe.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 885037f7-1c2b-4d7a-90d9-06b89be172f2
ms.openlocfilehash: 92d0834091a1f243df6be214f606fbf0093dca54
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244554"
---
# <a name="how-to-specify-a-service-binding-in-configuration"></a>Comment : spécifier une liaison de service dans la configuration
Dans cet exemple, un contrat `ICalculator` est défini pour un service de calculatrice de base, le service est implémenté dans la classe `CalculatorService`, puis son point de terminaison est configuré dans le fichier Web.config, où il est spécifié que le service utilise <xref:System.ServiceModel.BasicHttpBinding>. Pour obtenir une description de la façon de configurer ce service à l’aide de code au lieu d’une configuration, consultez [Comment : spécifier une liaison de service dans le code](how-to-specify-a-service-binding-in-code.md).  
  
 Il est généralement conseillé de spécifier de façon déclarative les informations de liaison et d'adresse dans la configuration plutôt que de manière impérative dans le code. La définition de points de terminaison dans le code est généralement peu pratique car les liaisons et les adresses pour un service déployé sont en général différentes de celles utilisées au cours du développement du service. Plus généralement, le fait de laisser les informations de liaison et d’adresse hors du code leur permet de changer sans nécessiter de recompilation ou de redéploiement de l’application.  
  
 Toutes les étapes de configuration suivantes peuvent être effectuées à l’aide de l' [outil Éditeur de configuration (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Pour obtenir la copie source de cet exemple, consultez [BasicBinding](./samples/basicbinding.md).  
  
## <a name="to-specify-the-basichttpbinding-to-use-to-configure-the-service"></a>Pour spécifier le BasicHttpBinding à utiliser pour configurer le service  
  
1. Définissez un contrat de service pour le type de service.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#1)]  
  
2. Implémentez le contrat de service dans une classe de service.  
  
     [!code-csharp[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_ConfigureServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_configureservicebinding/vb/source.vb#2)]  
  
    > [!NOTE]
    > Les informations de liaison ou d'adresse ne sont pas spécifiées dans l'implémentation du service. De plus, il n'est pas nécessaire d'écrire du code pour extraire ces informations du fichier de configuration.  
  
3. Créez un fichier Web.config pour configurer un point de terminaison pour le `CalculatorService` qui utilise le <xref:System.ServiceModel.WSHttpBinding>.  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name=" CalculatorService" >  

            <!-- Leave the address blank to be populated by default -->
            <!-- from the hosting environment,in this case IIS, so -->
            <!-- the address will just be that of the IIS Virtual -->
            <!-- Directory. -->

            <!-- Specify the binding configuration name for that -->
            <!-- binding type. This is optional but useful if you -->
            <!-- want to modify the properties of the binding. -->
            <!-- The bindingConfiguration name Binding1 is defined -->
            <!-- below in the bindings element. -->
            <endpoint
                address=""
                binding="wsHttpBinding"  
                bindingConfiguration="Binding1"  
                contract="ICalculator" />  
          </service>  
        </services>  
        <bindings>  
          <wsHttpBinding>  
            <binding name="Binding1">  
              <!-- Binding property values can be modified here. -->  
              <!-- See the next procedure. -->  
            </binding>  
          </wsHttpBinding>  
       </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4. Créez un fichier Service.svc qui contient la ligne suivante et placez-le dans votre répertoire virtuel des services Internet (IIS).  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>
    ```  
  
## <a name="to-modify-the-default-values-of-the-binding-properties"></a>Pour modifier les valeurs par défaut des propriétés de liaison  
  
1. Pour modifier l’une des valeurs de propriété par défaut de <xref:System.ServiceModel.WSHttpBinding> , créez un nouveau nom de configuration de liaison, `<binding name="Binding1">` dans l' [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) élément, puis définissez les nouvelles valeurs des attributs de la liaison dans cet élément de liaison. Par exemple, pour modifier les valeurs par défaut de délai d'attente d'ouverture et de fermeture de 1 minute à 2 minutes, ajoutez le code suivant au fichier de configuration.  
  
    ```xml  
    <wsHttpBinding>  
      <binding name="Binding1"  
               closeTimeout="00:02:00"  
               openTimeout="00:02:00">  
      </binding>  
    </wsHttpBinding>  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation de liaisons pour configurer des services et des clients](using-bindings-to-configure-services-and-clients.md)
- [Spécification d’une adresse de point de terminaison](specifying-an-endpoint-address.md)
