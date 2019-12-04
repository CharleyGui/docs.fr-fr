---
title: Références d'objet
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: bc9c318fc0e05f384a00df7cd1436a138315d880
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714680"
---
# <a name="object-references"></a>Références d'objet
Cet exemple montre comment transmettre des objets par référence entre le serveur et un client. L’exemple utilise des *réseaux sociaux*simulés. Un réseau social se compose d'une classe `Person` qui contient une liste d'amis dans laquelle chaque ami est une instance de la classe `Person`, contenant sa propre liste d'amis. Tous ces éléments constituent un graphique d'objets. Le service expose les opérations sur ces réseaux sociaux.  
  
 Dans cet exemple, le client est une application de console (.exe) et le service est hébergé par les services IIS (Internet Information Services).  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
## <a name="service"></a>Service  
 L'attribut `Person` est appliqué à la classe <xref:System.Runtime.Serialization.DataContractAttribute> et la valeur <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> est affectée au champ `true` pour le déclarer en tant que type de référence. L'attribut <xref:System.Runtime.Serialization.DataMemberAttribute>. est appliqué à toutes les propriétés.  
  
```csharp
[DataContract(IsReference=true)]  
public class Person  
{  
    string name;  
    string location;  
    string gender;  
    int age;  
    List<Person> friends;  
    [DataMember()]  
    public string Name  
    {  
        get { return name; }  
        set { name = value; }  
    }  
    [DataMember()]  
    public string Location  
    {  
        get { return location; }  
        set { location = value; }  
    }  
    [DataMember()]  
    public string Gender  
    {  
        get { return gender; }  
        set { gender = value; }  
    }  
…  
}  
```  
  
 L'opération `GetPeopleInNetwork` prend un paramètre du type `Person` et retourne toutes les personnes du réseau, c'est-à-dire toutes les personnes de la liste `friends`, les amis des amis, etc., sans doublons.  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 L'opération `GetMutualFriends` prend un paramètre du type `Person` et retourne tous les amis de la liste qui comportent également cette personne dans leur liste `friends`.  
  
```csharp
public List<Person> GetMutualFriends(Person p)  
{  
    List<Person> mutual = new List<Person>();  
    foreach (Person friend in p.Friends)  
    {  
        if (friend.Friends.Contains(p))  
            mutual.Add(friend);  
    }  
    return mutual;  
}  
```  
  
 L'opération `GetCommonFriends` prend une liste du type `Person`. Cette liste doit normalement contenir deux objets `Person`. L'opération retourne la liste des objets `Person` qui se trouvent dans les listes `friends` des deux objets `Person` de la liste d'entrée.  
  
```csharp
public List<Person> GetCommonFriends(List<Person> people)  
{  
    List<Person> common = new List<Person>();  
    foreach (Person friend in people[0].Friends)  
        if (people[1].Friends.Contains(friend))  
            common.Add(friend);  
    return common;  
}  
```  
  
## <a name="client"></a>Client  
 Le proxy client est créé à l’aide de la fonctionnalité **Ajouter une référence de service** de Visual Studio.  
  
 Un réseau social qui se compose de cinq objets `Person` est créé. Le client appelle chacune des trois méthodes dans le service.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Cet exemple se trouve dans le répertoire suivant.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [Références d’objets interopérables](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
