---
title: Utilisation de points de terminaison standard
ms.date: 03/30/2017
ms.assetid: ecd6a62f-9619-4778-a497-6f888087a9ea
ms.openlocfilehash: 2b210bfe683669aeebf54a1701f07d492e6abdb4
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715344"
---
# <a name="usage-of-standard-endpoints"></a>Utilisation de points de terminaison standard

Cet exemple montre comment utiliser des points de terminaison standard dans des fichiers de configuration de service. Un point de terminaison standard permet à l’utilisateur de simplifier des définitions de point de terminaison en utilisant une propriété unique pour décrire une combinaison adresse, liaison et contrat avec les propriétés supplémentaires qui lui sont associées. Cet exemple montre comment définir et implémenter un point de terminaison standard personnalisé et comment définir des propriétés spécifiques dans le point de terminaison.

## <a name="sample-details"></a>Détails de l'exemple

Les points de terminaison de service peuvent être spécifiés en fournissant trois paramètres : adresse, liaison et contrat. D'autres paramètres peuvent être fournis : configuration du comportement, en-têtes, URI d'écoute, et ainsi de suite. Il peut arriver que certains ou l’ensemble des adresses, liaisons et contrats aient des valeurs qui ne peuvent pas changer. C'est pourquoi il est possible d'utiliser des points de terminaison standard. Les points de terminaison d'échange de métadonnées et de découverte en sont des exemples. Les points de terminaison standard facilitent également l'utilisation en autorisant la configuration de points de terminaison de service sans avoir à fournir des informations d'une nature fixe ou à créer leurs propres points de terminaison standard, afin, par exemple, de faciliter l'utilisation en fournissant un jeu raisonnable de valeurs par défaut, ce qui réduit les commentaires des fichiers de configuration.

Cet exemple se compose de deux projets : le service qui définit deux points de terminaison standard et le client qui communique avec ce service. La façon dont les points de terminaison standard du service sont définis dans le fichier de configuration est illustrée dans l'exemple suivant.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <extensions>
      <endpointExtensions>
        <add name="customEndpoint" type="Microsoft.Samples.StandardEndpoints.CustomEndpointCollectionElement, service" />
      </endpointExtensions>
    </extensions>
    <services>
      <service name="Microsoft.Samples.StandardEndpoints.CalculatorService">
        <endpoint address="http://localhost:8000/Samples/Service.svc/customEndpoint" contract="Microsoft.Samples.StandardEndpoints.ICalculator" kind="customEndpoint" />
        <endpoint kind="mexEndpoint" />
      </service>
    </services>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <serviceMetadata httpGetEnabled="True"/>
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <standardEndpoints>
      <customEndpoint>
        <standardEndpoint property="True" />
      </customEndpoint>
    </standardEndpoints>
  </system.serviceModel>
</configuration>
```

Le premier point de terminaison défini pour le service est du genre `customEndpoint` (dont la définition est visible dans la section `<standardEndpoints>`) où la valeur `property` est affectée à la propriété `true`. C'est le cas d'un point de terminaison personnalisé avec une nouvelle propriété. Le deuxième point de terminaison correspond à un point de terminaison de métadonnées, où les valeurs d’adresse, de liaison et de contrat sont fixes.

Pour définir l'élément du point de terminaison standard, une classe qui dérive de `StandardEndpointElement` doit être créée. Dans le cas de cet exemple, la classe `CustomEndpointElement` a été définie comme indiqué dans l'exemple suivant.

```csharp
public class CustomEndpointElement : StandardEndpointElement
{
    public bool Property
    {
        get { return (bool)base["property"]; }
        set { base["property"] = value; }
    }

    protected override ConfigurationPropertyCollection Properties
    {
        get
        {
            ConfigurationPropertyCollection properties = base.Properties;
            properties.Add(new ConfigurationProperty("property", typeof(bool), false, ConfigurationPropertyOptions.None));
            return properties;
        }
    }

    protected override Type EndpointType
    {
        get { return typeof(CustomEndpoint); }
    }

    protected override ServiceEndpoint CreateServiceEndpoint(ContractDescription contract)
    {
        return new CustomEndpoint();
    }

    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ServiceEndpointElement serviceEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    protected override void OnApplyConfiguration(ServiceEndpoint endpoint, ChannelEndpointElement channelEndpointElement)
    {
        CustomEndpoint customEndpoint = (CustomEndpoint)endpoint;
        customEndpoint.Property = this.Property;
    }

    protected override void OnInitializeAndValidate(ServiceEndpointElement serviceEndpointElement)
    {
    }

    protected override void OnInitializeAndValidate(ChannelEndpointElement channelEndpointElement)
    {
    }
}
```

Dans la fonction `CreateServiceEndpoint`, un objet `CustomEndpoint` est créé. Sa définition est illustrée dans l’exemple suivant :

```csharp
public class CustomEndpoint : ServiceEndpoint
{
    public CustomEndpoint()
        : this(string.Empty)
    {
    }

    public CustomEndpoint(string address)
        : this(address, ContractDescription.GetContract(typeof(ICalculator)))
    {
    }

    public CustomEndpoint(string address, ContractDescription contract)
        : base(contract)
    {
        this.Binding = new BasicHttpBinding();
        this.IsSystemEndpoint = false;
    }

    public bool Property
    {
        get;
        set;
    }
}
```

 Pour permettre la communication entre service et client, une référence au service est créée dans le client. Lorsque l'exemple est généré et exécuté, le service s'exécute et le client communique avec lui. Notez que la référence de service doit être mise à jour à chaque modification du service.

#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple

1. À l’aide de Visual Studio 2012, ouvrez le fichier StandardEndpoints. sln.

2. Permettez à plusieurs projets de démarrer.

    1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur la solution points de terminaison standard, puis sélectionnez **Propriétés**.

    2. Dans **Propriétés communes**, sélectionnez **projet de démarrage**, puis cliquez sur **plusieurs projets de démarrage**.

    3. Déplacez le projet de service au début de la liste, avec l' **action** définie sur **Démarrer**.

    4. Déplacez le projet client après le projet de service, également avec l' **action** définie sur **Démarrer**.

         De cette façon, le projet Client est exécuté après le projet Service.

3. Pour exécuter la solution, appuyez sur F5.

> [!NOTE]
> Si ces étapes ne fonctionnent pas, assurez-vous que votre environnement a été correctement configuré, en procédant comme suit :
>
> 1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).
> 2. Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).
> 3. Pour exécuter l’exemple dans une seule ou plusieurs configurations d’ordinateur, suivez les instructions de [la](running-the-samples.md)procédure d’exécution des exemples de Windows Communication Foundation.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\StandardEndpoints`
