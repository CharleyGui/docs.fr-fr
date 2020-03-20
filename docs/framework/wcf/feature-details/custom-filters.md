---
title: Filtres personnalisés
ms.date: 03/30/2017
ms.assetid: 97cf247d-be0a-4057-bba9-3be5c45029d5
ms.openlocfilehash: ae020173544372c3ce097c8ac57e53f3fde37514
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185209"
---
# <a name="custom-filters"></a>Filtres personnalisés
Les filtres personnalisés vous permettent de définir une logique de correspondance qui ne peut pas être réalisée à l'aide des filtres de messages fournis par le système. Par exemple, vous pouvez créer un filtre personnalisé qui hache un élément de message particulier, puis examine la valeur pour déterminer si le filtre doit retourner la valeur true ou false.  
  
## <a name="implementation"></a>Implémentation  
 Un filtre personnalisé est une implémentation de la classe de base abstraite <xref:System.ServiceModel.Dispatcher.MessageFilter>. Lors de l'implémentation de votre filtre personnalisé, le constructeur peut éventuellement accepter un paramètre de chaîne unique. Ce paramètre contient les informations de configuration transmises au constructeur MessageFilter, afin de fournir les valeurs ou la configuration nécessaires au filtre pour effectuer des correspondances lors de l'exécution. Par exemple, cela permet de fournir une valeur que le filtre cherche dans le message qui est évalué. L'exemple suivant montre une implémentation de base d'un filtre de messages personnalisé qui accepte un paramètre de chaîne :  
  
```csharp  
public class MyMessageFilter: MessageFilter  
{  
    string filterData;  
    public MyMessageFilter(string filterData)  
    {  
        if(string.IsNullOrEmpty(filterData)  
            throw new ArgumentNullException("filterData");  
        this.filterData=filterData;  
    }  
    public override bool Match(System.ServiceModel.Channels.Message message)  
    {  
        ...  
        return retValue;  
    }  
    public override bool Match(System.ServiceModel.Channels.MessageBuffer buffer)  
    {  
        ...  
        return retValue;  
    }  
}  
```  
  
> [!NOTE]
> Dans une implémentation réelle, la méthode Match contient une logique qui examinera le message pour déterminer si ce filtre de message doit revenir **vrai** ou **faux**.  
  
### <a name="performance"></a>Performances  
 Lors de l'implémentation d'un filtre personnalisé, il est important de prendre en considération le temps maximal nécessaire au filtre pour procéder à l'évaluation d'un message. Dans la mesure où un message peut être évalué selon plusieurs filtres avant qu'une correspondance ne soit trouvée, il est essentiel de s'assurer que la demande du client n'expirera pas avant l'évaluation de tous les filtres. Par conséquent, un filtre personnalisé doit contenir uniquement le code nécessaire pour évaluer le contenu ou les attributs d'un message afin de déterminer s'il correspond aux critères de filtre.  
  
 En règle générale, lors de l'implémentation d'un filtre personnalisé, il convient d'éviter :  
  
- les E/S, comme l'enregistrement de données sur un disque ou dans une base de données ;  
  
- un traitement inutile, comme une boucle sur plusieurs enregistrements d'un document ;  
  
- les opérations bloquantes, comme des appels qui impliquent l'obtention d'un verrou sur des ressources partagées ou la réalisation de recherches dans une base de données.  
  
 Avant d'utiliser un filtre personnalisé dans un environnement de production, vous devez exécuter des tests de performance pour déterminer la durée moyenne nécessaire au filtre pour évaluer un message. En combinaison avec le temps de traitement moyen des autres filtres utilisés dans la table de filtres, cela vous permettra de déterminer correctement la valeur maximale de délai d'attente qui doit être spécifiée par l'application cliente.  
  
## <a name="usage"></a>Usage  
 Afin d’utiliser votre filtre personnalisé avec le service de routage, vous devez l’ajouter à la table de filtre en spécifiant une nouvelle entrée de filtre du type "Custom", le nom de type entièrement qualifié du filtre de message, et le nom de votre assemblage.  Comme avec d'autres MessageFilters, vous pouvez spécifier le filterData de chaîne qui sera transmis au constructeur de votre filtre personnalisé.  
  
 Les exemples suivants montrent l'utilisation d'un filtre personnalisé avec le service de routage :  
  
```xml  
<!--ROUTING SECTION -->  
<routing>  
  <filters>  
    <filter name="CustomFilter1" filterType="Custom"
            customType="CustomAssembly.MyMessageFilter,
            CustomAssembly" filterData="custom data" />  
  </filters>  
  <filterTables>  
    <table name="routingTable1">  
      <filters>  
        <add filterName="CustomFilter1" endpointName="CalculatorService" />  
      </filters>  
    </table>  
  </filterTables>  
</routing>  
```  
  
```csharp  
RoutingConfiguration rc = new RoutingConfiguration();  
List<ServiceEndpoint> endpointList = new List<ServiceEndpoint>();  
endpointList.Add(client);  
rc.FilterTable.Add(new MyMessageFilter("CustomData"), endpointList);  
```
