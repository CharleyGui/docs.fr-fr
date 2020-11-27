---
title: Références d'objet
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: 55cadc908a3479ee3d104354bcbfd3ea49b15d07
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262370"
---
# <a name="object-references"></a><span data-ttu-id="daea6-102">Références d'objet</span><span class="sxs-lookup"><span data-stu-id="daea6-102">Object References</span></span>

<span data-ttu-id="daea6-103">Cet exemple montre comment transmettre des objets par référence entre le serveur et un client.</span><span class="sxs-lookup"><span data-stu-id="daea6-103">This sample demonstrates how to pass objects by references between server and client.</span></span> <span data-ttu-id="daea6-104">L’exemple utilise des *réseaux sociaux* simulés.</span><span class="sxs-lookup"><span data-stu-id="daea6-104">The sample uses simulated *social networks*.</span></span> <span data-ttu-id="daea6-105">Un réseau social se compose d'une classe `Person` qui contient une liste d'amis dans laquelle chaque ami est une instance de la classe `Person`, contenant sa propre liste d'amis.</span><span class="sxs-lookup"><span data-stu-id="daea6-105">A social network consists of a `Person` class that contains a list of friends in which each friend is an instance of the `Person` class, with its own list of friends.</span></span> <span data-ttu-id="daea6-106">Tous ces éléments constituent un graphique d'objets.</span><span class="sxs-lookup"><span data-stu-id="daea6-106">This creates a graph of objects.</span></span> <span data-ttu-id="daea6-107">Le service expose les opérations sur ces réseaux sociaux.</span><span class="sxs-lookup"><span data-stu-id="daea6-107">The service exposes operations on these social networks.</span></span>  
  
 <span data-ttu-id="daea6-108">Dans cet exemple, le client est une application de console (.exe) et le service est hébergé par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="daea6-108">In this sample, the service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="daea6-109">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="daea6-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="daea6-110">Service</span><span class="sxs-lookup"><span data-stu-id="daea6-110">Service</span></span>  

 <span data-ttu-id="daea6-111">L'attribut `Person` est appliqué à la classe <xref:System.Runtime.Serialization.DataContractAttribute> et la valeur <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> est affectée au champ `true` pour le déclarer en tant que type de référence.</span><span class="sxs-lookup"><span data-stu-id="daea6-111">The `Person` class has the <xref:System.Runtime.Serialization.DataContractAttribute> attribute applied, with the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> field set to `true` to declare it as a reference type.</span></span> <span data-ttu-id="daea6-112">L'attribut <xref:System.Runtime.Serialization.DataMemberAttribute>. est appliqué à toutes les propriétés.</span><span class="sxs-lookup"><span data-stu-id="daea6-112">All properties have the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute applied.</span></span>  
  
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
  
 <span data-ttu-id="daea6-113">L'opération `GetPeopleInNetwork` prend un paramètre du type `Person` et retourne toutes les personnes du réseau, c'est-à-dire toutes les personnes de la liste `friends`, les amis des amis, etc., sans doublons.</span><span class="sxs-lookup"><span data-stu-id="daea6-113">The `GetPeopleInNetwork` operation takes a parameter of type `Person` and returns all the people in the network; that is, all the people in the `friends` list, the friend's friends, and so on, without duplicates.</span></span>  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 <span data-ttu-id="daea6-114">L'opération `GetMutualFriends` prend un paramètre du type `Person` et retourne tous les amis de la liste qui comportent également cette personne dans leur liste `friends`.</span><span class="sxs-lookup"><span data-stu-id="daea6-114">The `GetMutualFriends` operation takes a parameter of type `Person` and returns all the friends in the list who also have this person in their `friends` list.</span></span>  
  
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
  
 <span data-ttu-id="daea6-115">L'opération `GetCommonFriends` prend une liste du type `Person`.</span><span class="sxs-lookup"><span data-stu-id="daea6-115">The `GetCommonFriends` operation takes a list of type `Person`.</span></span> <span data-ttu-id="daea6-116">Cette liste doit normalement contenir deux objets `Person`.</span><span class="sxs-lookup"><span data-stu-id="daea6-116">The list is expected to have two `Person` objects in it.</span></span> <span data-ttu-id="daea6-117">L'opération retourne la liste des objets `Person` qui se trouvent dans les listes `friends` des deux objets `Person` de la liste d'entrée.</span><span class="sxs-lookup"><span data-stu-id="daea6-117">The operation returns a list of `Person` objects that are in the `friends` lists of both `Person` objects in the input list.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="daea6-118">Client</span><span class="sxs-lookup"><span data-stu-id="daea6-118">Client</span></span>  

 <span data-ttu-id="daea6-119">Le proxy client est créé à l’aide de la fonctionnalité **Ajouter une référence de service** de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="daea6-119">The client proxy is created using the **Add Service Reference** feature of Visual Studio.</span></span>  
  
 <span data-ttu-id="daea6-120">Un réseau social qui se compose de cinq objets `Person` est créé.</span><span class="sxs-lookup"><span data-stu-id="daea6-120">A social network that consists of five `Person` objects is created.</span></span> <span data-ttu-id="daea6-121">Le client appelle chacune des trois méthodes dans le service.</span><span class="sxs-lookup"><span data-stu-id="daea6-121">The client calls each of the three methods in the service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="daea6-122">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="daea6-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="daea6-123">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="daea6-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="daea6-124">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="daea6-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="daea6-125">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="daea6-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="daea6-126">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="daea6-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="daea6-127">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="daea6-127">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="daea6-128">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="daea6-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="daea6-129">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="daea6-129">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a><span data-ttu-id="daea6-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="daea6-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [<span data-ttu-id="daea6-131">Références d'objets interopérables</span><span class="sxs-lookup"><span data-stu-id="daea6-131">Interoperable Object References</span></span>](../feature-details/interoperable-object-references.md)
