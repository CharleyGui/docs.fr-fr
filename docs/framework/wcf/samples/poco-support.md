---
title: Prise en charge POCO
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: a9f8d185c58b22e68f7a8c11954e0e534c4bd48f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600462"
---
# <a name="poco-support"></a><span data-ttu-id="98851-102">Prise en charge POCO</span><span class="sxs-lookup"><span data-stu-id="98851-102">POCO Support</span></span>
<span data-ttu-id="98851-103">Cet exemple illustre la prise en charge de la sérialisation pour les types non marqués, c'est-à-dire les types auxquels aucun attribut de sérialisation n'a été appliqué. Ces types sont parfois appelés types POCO (Plain Old CLR Object).</span><span class="sxs-lookup"><span data-stu-id="98851-103">This sample demonstrates the serialization support for unmarked types; that is, types to which serialization attributes have not been applied, sometimes referred to as Plain Old CLR Object (POCO) types.</span></span> <span data-ttu-id="98851-104">Le <xref:System.Runtime.Serialization.DataContractSerializer> déduit un contrat de données pour tous les types non marqués publics qui ont un constructeur sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="98851-104">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract for all public unmarked types that have a parameterless constructor.</span></span> <span data-ttu-id="98851-105">Les contrats de données vous permettent de transférer des données structurées vers des services et à partir de ceux-ci.</span><span class="sxs-lookup"><span data-stu-id="98851-105">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="98851-106">Pour plus d’informations sur les types non marqués, consultez [types sérialisables](../feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="98851-106">For more information about unmarked types, see [Serializable Types](../feature-details/serializable-types.md).</span></span>  
  
 <span data-ttu-id="98851-107">Cet exemple est basé sur le [prise en main](getting-started-sample.md), mais utilise des nombres complexes au lieu de types numériques primitifs.</span><span class="sxs-lookup"><span data-stu-id="98851-107">This sample is based on the [Getting Started](getting-started-sample.md), but uses complex numbers instead of primitive numeric types.</span></span> <span data-ttu-id="98851-108">Elle est également similaire à l’exemple de [contrat de données de base](basic-data-contract.md) , à la différence que les <xref:System.Runtime.Serialization.DataContractAttribute> attributs et ne <xref:System.Runtime.Serialization.DataMemberAttribute> sont pas utilisés.</span><span class="sxs-lookup"><span data-stu-id="98851-108">It is also similar to the [Basic Data Contract](basic-data-contract.md) sample, except that the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes are not used.</span></span>  
  
 <span data-ttu-id="98851-109">Le client est une application de console (.exe) et le service est hébergé par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="98851-109">The service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="98851-110">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="98851-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="98851-111">La classe `ComplexNumber` est utilisée dans `ServiceContract`.</span><span class="sxs-lookup"><span data-stu-id="98851-111">The `ComplexNumber` class is used in the `ServiceContract`.</span></span> <span data-ttu-id="98851-112">Le type `ComplexNumber` ne comporte pas les attributs <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute>, comme indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="98851-112">The `ComplexNumber` type does not have the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes, as shown in the following sample code.</span></span> <span data-ttu-id="98851-113">Par défaut, l'ensemble des propriétés et des champs publics sont sérialisés.</span><span class="sxs-lookup"><span data-stu-id="98851-113">By default, all public properties and fields are serialized.</span></span>  
  
```csharp
public class ComplexNumber  
{  
    public double Real;  
    public double Imaginary;  
    public ComplexNumber()  
    {  
        Real = double.MinValue;  
        Imaginary = double.MinValue;  
    }  
    public ComplexNumber(double real, double imaginary)  
    {  
        this.Real = real;  
        this.Imaginary = imaginary;  
    }  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="98851-114">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="98851-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="98851-115">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="98851-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="98851-116">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="98851-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="98851-117">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="98851-117">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="98851-118">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="98851-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="98851-119">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="98851-119">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="98851-120">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="98851-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="98851-121">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="98851-121">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a><span data-ttu-id="98851-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98851-122">See also</span></span>

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- [<span data-ttu-id="98851-123">Types sérialisables</span><span class="sxs-lookup"><span data-stu-id="98851-123">Serializable Types</span></span>](../feature-details/serializable-types.md)
