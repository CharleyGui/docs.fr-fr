---
title: 'Procédure : configurer des paramètres de service COM+'
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], configuring service settings
ms.assetid: f42a55a8-3af8-4394-9fdd-bf12a93780eb
ms.openlocfilehash: 58845ab7b9da7377f4fdaa7da13e7c407226d63c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912206"
---
# <a name="how-to-configure-com-service-settings"></a><span data-ttu-id="6dd60-102">Procédure : configurer des paramètres de service COM+</span><span class="sxs-lookup"><span data-stu-id="6dd60-102">How to: Configure COM+ Service Settings</span></span>
<span data-ttu-id="6dd60-103">Lorsqu'une interface d'application est ajoutée ou supprimée en utilisant l'outil de configuration de service COM+, la configuration de service Web est mise à jour dans le fichier de configuration de l'application.</span><span class="sxs-lookup"><span data-stu-id="6dd60-103">When an application interface is added or removed by using the COM+ Service Configuration tool, the Web service configuration is updated within the application's configuration file.</span></span> <span data-ttu-id="6dd60-104">Dans le mode hébergé par com+, le fichier application. config est placé dans le répertoire racine de l’application\\(%ProgramFiles%\ComPlus applications {AppID} est la valeur par défaut).</span><span class="sxs-lookup"><span data-stu-id="6dd60-104">In the COM+ hosted mode, the Application.config file is placed in the Application Root Directory (%PROGRAMFILES%\ComPlus Applications\\{appid} is the default).</span></span> <span data-ttu-id="6dd60-105">Dans l'un ou l'autre des modes hébergés sur le Web, le fichier Web.config est placé dans le répertoire vroot spécifié.</span><span class="sxs-lookup"><span data-stu-id="6dd60-105">In either of the Web-hosted modes, the Web.config file is placed in the specified vroot directory.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6dd60-106">La signature du message doit être utilisée pour éviter la falsification des messages entre un client et un serveur.</span><span class="sxs-lookup"><span data-stu-id="6dd60-106">Message signing should be used to protect against tampering of messages between a client and a server.</span></span> <span data-ttu-id="6dd60-107">De plus, le chiffrement de la couche transport ou message doit être utilisé pour se protéger contre la divulgation d'informations de messages entre un client et un serveur.</span><span class="sxs-lookup"><span data-stu-id="6dd60-107">Also, message or transport layer encryption should be used to protect against information disclosure from messages between a client and a server.</span></span> <span data-ttu-id="6dd60-108">Comme pour les services Windows Communication Foundation (WCF), vous devez utiliser la limitation pour limiter le nombre d’appels simultanés, de connexions, d’instances et d’opérations en attente.</span><span class="sxs-lookup"><span data-stu-id="6dd60-108">As with Windows Communication Foundation (WCF) services, you should use throttling to limit the number of concurrent calls, connections, instances, and pending operations.</span></span> <span data-ttu-id="6dd60-109">Elle permet d'empêcher la surconsommation de ressources.</span><span class="sxs-lookup"><span data-stu-id="6dd60-109">This helps prevent over-consumption of resources.</span></span> <span data-ttu-id="6dd60-110">La fonctionnalité de limitation est spécifiée à l'aide des paramètres de fichier de configuration de service.</span><span class="sxs-lookup"><span data-stu-id="6dd60-110">Throttling behavior is specified through service configuration file settings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6dd60-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="6dd60-111">Example</span></span>  
 <span data-ttu-id="6dd60-112">Prenons l'exemple d'un composant qui implémente l'interface suivante :</span><span class="sxs-lookup"><span data-stu-id="6dd60-112">Consider a component that implements the following interface:</span></span>  
  
```  
[Guid("C551FBA9-E3AA-4272-8C2A-84BD8D290AC7")]  
public interface IFinances  
{  
    string Debit(string accountNo, double amount);  
    string Credit(string accountNo, double amount);  
}  
```  
  
 <span data-ttu-id="6dd60-113">Si le composant est exposé en tant que service Web, le contrat de service correspondant qui est exposé, et auquel les clients doivent se conformer, est le suivant :</span><span class="sxs-lookup"><span data-stu-id="6dd60-113">If the component is exposed as a Web service, the corresponding service contract that is exposed, and that clients would need to conform to, is as follows:</span></span>  
  
```  
[ServiceContract(Session = true,  
Namespace = "http://tempuri.org/C551FBA9-E3AA-4272-8C2A-84BD8D290AC7",  
Name = "IFinances")]  
public interface IFinancesContract : IDisposable  
{  
    [OperationContract]  
    string Debit(string accountNo, double amount);  
    [OperationContract]  
    string Credit(string accountNo, double amount);  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="6dd60-114">IID fait partie intégrante de l'espace de noms initial pour le contrat.</span><span class="sxs-lookup"><span data-stu-id="6dd60-114">IID forms part of the initial namespace for the contract.</span></span>  
  
 <span data-ttu-id="6dd60-115">Les applications clientes qui utilisent ce service doivent se conformer à ce contrat et utiliser une liaison compatible avec celui spécifié dans la configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="6dd60-115">Client applications that use this service would need to conform to this contract, along with using a binding that is compatible with the one specified in the application configuration.</span></span>  
  
 <span data-ttu-id="6dd60-116">L'exemple de code suivant affiche un fichier de configuration par défaut.</span><span class="sxs-lookup"><span data-stu-id="6dd60-116">The following code example shows a default configuration file.</span></span> <span data-ttu-id="6dd60-117">En tant que service Web Windows Communication Foundation (WCF), il est conforme au schéma de configuration de modèle de service standard et peut être modifié de la même façon que les autres fichiers de configuration des services WCF.</span><span class="sxs-lookup"><span data-stu-id="6dd60-117">Being a Windows Communication Foundation (WCF) Web service, this conforms to the standard service model configuration schema and can be edited in the same way as other WCF services configuration files.</span></span>  
  
 <span data-ttu-id="6dd60-118">Les changements standard incluent :</span><span class="sxs-lookup"><span data-stu-id="6dd60-118">Typical modifications would include:</span></span>  
  
- <span data-ttu-id="6dd60-119">Remplacer l'adresse de point de terminaison de la forme par défaut ApplicationName/ComponentName/InterfaceName par une forme plus utilisable.</span><span class="sxs-lookup"><span data-stu-id="6dd60-119">Changing the endpoint address from the default ApplicationName/ComponentName/InterfaceName form to a more usable form.</span></span>  
  
- <span data-ttu-id="6dd60-120">La modification de l’espace de noms du service du `http://tempuri.org/InterfaceID` formulaire par défaut est plus appropriée.</span><span class="sxs-lookup"><span data-stu-id="6dd60-120">Modifying the namespace of the service from the default `http://tempuri.org/InterfaceID` form to a more relevant form.</span></span>  
  
- <span data-ttu-id="6dd60-121">Modifier le point de terminaison pour utiliser une liaison de transport différente.</span><span class="sxs-lookup"><span data-stu-id="6dd60-121">Changing the endpoint to use a different transport binding.</span></span>  
  
     <span data-ttu-id="6dd60-122">Dans le cas hébergé par COM+, le transport de canaux nommés est utilisé par défaut, mais un transport off-machine, tel que TCP, peut être utilisé à la place.</span><span class="sxs-lookup"><span data-stu-id="6dd60-122">In the COM+-hosted case, the named pipes transport is used by default, but an off-machine transport like TCP can be used instead.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <netNamedPipeBinding>  
                <binding name="comNonTransactionalBinding" />  
                <binding name="comTransactionalBinding" transactionFlow="true" />  
            </netNamedPipeBinding>  
        </bindings>  
        <comContracts>  
            <comContract contract="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"  
                name="IFinances" namespace="http://tempuri.org/C551FBA9-E3AA-4272-8C2A-84BD8D290AC7"  
                requiresSession="true">  
                <exposedMethods>  
                    <add exposedMethod="Debit" />  
                    <add exposedMethod="Credit" />  
                </exposedMethods>  
            </comContract>  
        </comContracts>  
        <services>  
            <service name="{DCDB24CC-0B19-4534-95CD-FBBFF4D67DD9},{C942B840-AD54-4A44-B5F7-928130980AB9}">  
                <endpoint address="IFinances" binding="netNamedPipeBinding" bindingConfiguration="comNonTransactionalBinding"  
                    contract="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}" />  
                <host>  
                    <baseAddresses>  
                        <add baseAddress="net.pipe://localhost/ServiceModelDocSampleApp/ServiceModelDocSample.esFinance" />  
                    </baseAddresses>  
                </host>  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6dd60-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6dd60-123">See also</span></span>

- [<span data-ttu-id="6dd60-124">Intégration à des applications COM+</span><span class="sxs-lookup"><span data-stu-id="6dd60-124">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
