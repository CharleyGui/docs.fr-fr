---
title: 'Procédure : utiliser des filtres'
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: 149c0809820d6a4a9c8dabfb545258b9a3ffb40b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280843"
---
# <a name="how-to-use-filters"></a>Procédure : utiliser des filtres

Cette rubrique décrit les étapes de base requises pour créer une configuration de routage qui utilise plusieurs filtres. Dans cet exemple, les messages sont routés vers deux implémentations d'un service de calculatrice, regularCalc et roundingCalc. Les deux implémentations prennent en charge les mêmes opérations ; toutefois, l'un des services arrondit tous les calculs à la valeur entière la plus proche avant de les retourner. Une application cliente doit être en mesure d'indiquer s'il faut utiliser la version arrondie de ce service ; si aucune préférence de service n'est exprimée, le message est équilibré entre les deux services. Les opérations exposées par les deux services sont :  
  
- Ajouter  
  
- Soustraire  
  
- Multiplier  
  
- Diviser  
  
 Étant donné que les deux services implémentent les mêmes opérations, vous ne pouvez pas utiliser le filtre Action, car l'action spécifiée dans le message ne sera pas unique. Vous devez plutôt effectuer un travail supplémentaire pour vérifier que les messages sont routés vers les points de terminaison appropriés.  
  
### <a name="determine-unique-data"></a>Déterminer des données uniques  
  
1. Comme les deux implémentations de service gèrent les mêmes opérations et sont pour l'essentiel identiques en dehors des données qu'elles retournent, les données de base contenues dans les messages envoyés à partir d'applications clientes ne sont pas assez uniques pour vous permettre de déterminer comment router la demande. Mais si l'application cliente ajoute une valeur d'en-tête unique au message, vous pouvez utiliser cette valeur pour déterminer comment le message doit être routé.  
  
     Pour cet exemple, si l'application cliente a besoin que le message soit traité par la calculatrice d'arrondi, elle ajoute un en-tête personnalisé à l'aide du code suivant :  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     Vous pouvez maintenant utiliser le filtre XPath pour vérifier la présence de cet en-tête dans les messages et router ceux qui le contiennent vers le service roundCalc.  
  
2. En outre, le service de routage expose deux points de terminaison de service virtuels qui peuvent être utilisés avec les filtres EndpointName, EndpointAddress ou PrefixEndpointAddress, pour router de manière unique les messages entrants vers une implémentation de calculatrice spécifique, en fonction du point de terminaison auquel l'application cliente soumet la demande.  
  
### <a name="define-endpoints"></a>Définir des points de terminaison  
  
1. Lorsque vous définissez les points de terminaison utilisés par le service de routage, vous devez d'abord déterminer la forme du canal utilisé par vos clients et vos services. Dans ce scénario, les deux services de destination utilisent un modèle demande-réponse, donc la forme <xref:System.ServiceModel.Routing.IRequestReplyRouter> est utilisée. L'exemple suivant définit les points de terminaison de service exposés par le service de routage.  
  
    ```xml  
    <services>  
          <service behaviorConfiguration="routingConfiguration"  
                   name="System.ServiceModel.Routing.RoutingService">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost/routingservice/router" />  
              </baseAddresses>  
            </host>  
            <!--Set up the inbound endpoints for the Routing Service-->  
            <!--first create the general router endpoint-->  
            <endpoint address="general"  
                      binding="wsHttpBinding"  
                      name="routerEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--create a virtual endpoint for the regular calculator service-->  
            <endpoint address="regular/calculator"  
                      binding="wsHttpBinding"  
                      name="calculatorEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--now create a virtual endpoint for the rounding calculator-->  
            <endpoint address="rounding/calculator"  
                      binding="wsHttpBinding"  
                      name="roundingEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
          </service>  
    </services>  
    ```  
  
     Avec cette configuration, le service de routage expose trois points de terminaison distincts. En fonction des choix d'exécution, l'application cliente envoie des messages à l'une de ces adresses. Les messages arrivant à l’un des points de terminaison de service « virtuels » (« rounding/Calculator » ou « Regular/Calculator ») sont transmis à l’implémentation de calculatrice correspondante. Si l'application cliente n'envoie pas la demande à un point de terminaison particulier, le message est adressé au point de terminaison général. Indépendamment du point de terminaison retenu, l'application cliente peut choisir également d'inclure l'en-tête personnalisé pour indiquer que le message doit être envoyé à l'implémentation de la calculatrice d'arrondi.  
  
2. L'exemple suivant définit les points de terminaison clients (destination) vers lesquels le service de routage route des messages.  
  
    ```xml  
    <client>  
          <endpoint name="regularCalcEndpoint"  
                    address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
  
          <endpoint name="roundingCalcEndpoint"  
                    address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
    </client>  
    ```  
  
     Ces points de terminaison sont utilisés dans la table de filtres pour indiquer le point de terminaison de destination auquel le message est envoyé lorsqu'il correspond à un filtre spécifique.  
  
### <a name="define-filters"></a>Définir les filtres  
  
1. Pour acheminer les messages en fonction de l’en-tête personnalisé « RoundingCalculator » que l’application cliente ajoute au message, définissez un filtre qui utilise une requête XPath pour vérifier la présence de cet en-tête. Étant donné que cet en-tête est défini à l’aide d’un espace de noms personnalisé, ajoutez également une entrée d’espace de noms qui définit un préfixe d’espace de noms personnalisé « Custom » qui est utilisé dans la requête XPath. L'exemple suivant définit la section de routage nécessaire, la table d'espace de noms et le filtre XPath.  
  
    ```xml  
    <routing>  
          <!-- use the namespace table element to define a prefix for our custom namespace-->  
          <namespaceTable>  
            <add prefix="custom" namespace="http://my.custom.namespace/"/>  
          </namespaceTable>  
          <filters>  
            <!--define the different message filters-->  
            <!--define an xpath message filter to look for the custom header coming from the client-->  
            <filter name="XPathFilter" filterType="XPath"
                    filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
          </filters>  
    </routing>  
    ```  
  
     Ce **MessageFilter** recherche un en-tête RoundingCalculator dans le message qui contient la valeur « arrondissement ». Cet en-tête est défini par le client pour indiquer que le message doit être routé vers le service roundingCalc.  
  
    > [!NOTE]
    > Le préfixe d’espace de noms S12 est défini par défaut dans la table d’espace de noms et représente l’espace de noms `http://www.w3.org/2003/05/soap-envelope` .
  
2. Vous devez également définir des filtres qui recherchent des messages reçus sur les deux points de terminaison virtuels. Le premier point de terminaison virtuel est le point de terminaison « Regular/Calculator ». Le client peut envoyer des demandes à ce point de terminaison pour indiquer que le message doit être routé vers le service regularCalc. La configuration suivante définit un filtre qui utilise l'objet <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> pour déterminer si le message est arrivé par un point de terminaison dont le nom est spécifié dans FilterData.  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     Si un message est reçu par le point de terminaison de service nommé « calculatorEndpoint », ce filtre prend la valeur `true` .  
  
3. Ensuite, définissez un filtre qui recherche les messages envoyés à l'adresse du roundingEndpoint. Le client peut envoyer des demandes à ce point de terminaison pour indiquer que le message doit être routé vers le service roundingCalc. La configuration suivante définit un filtre qui utilise <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> pour déterminer si le message est arrivé au point de terminaison « arrondi/calculatrice ».  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     Si un message est reçu à une adresse qui commence par `http://localhost/routingservice/router/rounding/` , ce filtre prend la **valeur true**. Étant donné que l’adresse de base utilisée par cette configuration est `http://localhost/routingservice/router` et que l’adresse spécifiée pour le roundingEndpoint est « arrondi/calculatrice », l’adresse complète utilisée pour communiquer avec ce point de terminaison est `http://localhost/routingservice/router/rounding/calculator` , qui correspond à ce filtre.  
  
    > [!NOTE]
    > Le filtre PrefixEndpointAddress n'évalue pas le nom d'hôte lorsqu'il effectue une correspondance, parce qu'il peut être fait référence à un hôte unique à l'aide de divers noms d'hôte qui tous peuvent constituer des moyens valides de faire référence à l'hôte à partir de l'application cliente. Par exemple, tous les éléments suivants peuvent faire référence au même hôte :  
    >
    > - localhost  
    > - 127.0.0.1  
    > - `www.contoso.com`  
    > - ContosoWeb01  
  
4. Le filtre définitif doit prendre en charge le routage des messages qui arrivent au point de terminaison général sans en-tête personnalisé. Pour ce scénario, les messages doivent alterner entre les services roundingCalc et regularCalc. Pour prendre en charge le routage par tourniquet (Round Robin) de ces messages, utilisez un filtre personnalisé qui permet à une instance de filtre de correspondre pour chaque message traité.  Les éléments suivants définissent deux instances d'un RoundRobinMessageFilter, qui sont regroupées pour indiquer qu'elles doivent alterner entre elles.  
  
    ```xml  
    <!-- Set up the custom message filters.  In this example,   
         we'll use the example round robin message filter,   
         which alternates between the references-->  
    <filter name="RoundRobinFilter1" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    <filter name="RoundRobinFilter2" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    ```  
  
     Au moment de l’exécution, ce type de filtre alterne entre toutes les instances de filtre définies de ce type qui sont configurées comme un même groupe dans une collection. Cela entraîne le remplacement des messages traités par ce filtre personnalisé entre le retour `true` de `RoundRobinFilter1` et de `RoundRobinFilter2` .  
  
### <a name="define-filter-tables"></a>Définir des tables de filtres  
  
1. Pour associer les filtres à des points de terminaison clients spécifiques, vous devez les placer dans une table de filtres. Cet exemple de scénario utilise également des paramètres de priorité du filtre, qui sont facultatifs et vous permettent d'indiquer l'ordre dans lequel les filtres sont traités. Si aucune priorité de filtre n'est spécifiée, tous les filtres sont évalués simultanément.  
  
    > [!NOTE]
    > Si la spécification d'une priorité de filtre vous permet de contrôler l'ordre dans lequel les filtres sont traités, elle peut aussi nuire aux performances du service de routage. Si possible, construisez la logique de filtre de manière à ne pas être obligé de recourir aux priorités de filtre.  
  
     Les éléments suivants définissent la table de filtres et ajoutent la valeur « XPathFilter » définie précédemment à la table, avec une priorité de 2. Cette entrée spécifie également que si le `XPathFilter` correspond au message, le message est routé vers le `roundingCalcEndpoint` .  
  
    ```xml  
    <routing>  
    ...      <filters>  
    ...      </filters>  
          <filterTables>  
            <table name="filterTable1">  
              <entries>  
                <!--add the filters to the message filter table-->  
                <!--first look for the custom header, and if we find it,  
                    send the message to the rounding calc endpoint-->  
                <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
              </entries>  
            </table>  
          </filterTables>  
    </routing>  
    ```  
  
     Lors de la spécification d'une priorité de filtre, les filtres de priorité plus élevée sont évalués en premier. Si un ou plusieurs filtres d'un niveau de priorité spécifique correspondent, aucun filtre de niveau de priorité plus faible ne sera évalué. Pour ce scénario, 2 est la priorité spécifiée la plus élevée et c'est la seule entrée de filtre à ce niveau.  
  
2. Les entrées de filtre ont été définies pour vérifier si un message est reçu sur un point de terminaison spécifique, en contrôlant le nom du point de terminaison ou le préfixe d'adresse. Les entrées suivantes ajoutent ces deux entrées de filtre à la table de filtres et les associent aux points de terminaison de destination vers lesquels le message sera routé. Une priorité de valeur 1 est attribuée à ces filtres pour indiquer qu'ils ne doivent s'exécuter que si le filtre XPath précédent ne correspondait pas au message.  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     Puisque ces filtres ont une priorité de filtre de 1, ils ne seront évalués que si le filtre de niveau de priorité 2 ne correspond pas au message. Comme les deux filtres ont le même niveau de priorité, ils seront évalués simultanément. Puisque les deux filtres s'excluent mutuellement, un seul d'entre eux peut correspondre à un message.  
  
3. Si un message ne correspond à aucun des filtres précédents, cela signifie que le message a été reçu via le point de terminaison de service générique et ne contenait aucune information d'en-tête indiquant où le router. Ces messages doivent être contrôlés par le filtre personnalisé, qui équilibre leur charge entre les deux services de calculatrice. L'exemple suivant montre comment ajouter les entrées de filtre à la table de filtres ; chaque filtre est associé à l'un des deux points de terminaison de destination.  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     Ces entrées spécifient une priorité de niveau 0, elles ne seront donc évaluées que si aucun filtre de priorité plus élevée ne correspond au message. De même, puisque les deux ont la même priorité, elles sont évaluées simultanément.  
  
     Comme indiqué précédemment, le filtre personnalisé utilisé par ces définitions de filtre évalue seulement l'une d'entre elles comme `true` pour chaque message reçu. Comme deux filtres seulement sont définis à l'aide de ce filtre, avec le même paramètre de groupe spécifié, le résultat est que le service de routage effectue les envois en alternance au regularCalcEndpoint et au RoundingCalcEndpoint.  
  
4. Pour évaluer les messages en fonction des filtres, la table de filtres doit être d'abord associée aux points de terminaison de service qui seront utilisés pour recevoir des messages.  L'exemple suivant montre comment associer la table de routage aux points de terminaison de service à l'aide du comportement de routage :  
  
    ```xml  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="example"></a> Exemple  

 L'intégralité du fichier de configuration est présentée ci-dessous.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright (c) Microsoft Corporation. All rights reserved -->  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoints for the Routing Service-->  
        <!--first create the general router endpoint-->  
        <endpoint address="general"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--create a virtual endpoint for the regular calculator service-->  
        <endpoint address="regular/calculator"  
                  binding="wsHttpBinding"  
                  name="calculatorEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--now create a virtual endpoint for the rounding calculator-->  
        <endpoint address="rounding/calculator"  
                  binding="wsHttpBinding"  
                  name="roundingEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
      </service>  
    </services>  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
    <client>  
<!--set up the destination endpoints-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="roundingCalcEndpoint"  
                address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
      <namespaceTable>  
        <add prefix="custom" namespace="http://my.custom.namespace/"/>  
      </namespaceTable>  
      <filters>  
        <!--define the different message filters-->  
        <!--define an xpath message filter to look for the custom header coming from the client-->  
        <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
  
        <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
        <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
  
        <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
        <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress" filterData="http://localhost/routingservice/router/rounding/"/>  
  
        <!--Set up the custom message filters.  In this example, we'll use the example round robin message filter, which alternates between the references-->  
        <filter name="RoundRobinFilter1" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
        <filter name="RoundRobinFilter2" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
      </filters>  
      <filterTables>  
        <table name="filterTable1">  
          <entries>  
            <!--add the filters to the message filter table-->  
            <!--first look for the custom header, and if we find it, send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
  
            <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
            <!--we determine this through the endpoint name, or through the address prefix-->  
            <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
            <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
  
            <!--if none of the other filters have matched, this message showed up on the default router endpoint, with no custom header-->  
            <!--round robin these requests between the two services-->  
            <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
            <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
          </entries>  
        </table>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Services de routage](../samples/routing-services.md)
