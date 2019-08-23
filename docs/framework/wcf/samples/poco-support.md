---
title: Prise en charge POCO
ms.date: 03/30/2017
ms.assetid: 3846ca73-2819-4ca2-8367-dc739dde5a5b
ms.openlocfilehash: 90b55362c1958ea5677e3bc0cdca906bb3af6b3d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965551"
---
# <a name="poco-support"></a><span data-ttu-id="37ff5-102">Prise en charge POCO</span><span class="sxs-lookup"><span data-stu-id="37ff5-102">POCO Support</span></span>
<span data-ttu-id="37ff5-103">Cet exemple illustre la prise en charge de la sérialisation pour les types non marqués, c'est-à-dire les types auxquels aucun attribut de sérialisation n'a été appliqué. Ces types sont parfois appelés types POCO (Plain Old CLR Object).</span><span class="sxs-lookup"><span data-stu-id="37ff5-103">This sample demonstrates the serialization support for unmarked types; that is, types to which serialization attributes have not been applied, sometimes referred to as Plain Old CLR Object (POCO) types.</span></span> <span data-ttu-id="37ff5-104">Le <xref:System.Runtime.Serialization.DataContractSerializer> déduit un contrat de données pour tous les types non marqués publics qui ont un constructeur sans paramètre.</span><span class="sxs-lookup"><span data-stu-id="37ff5-104">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract for all public unmarked types that have a parameterless constructor.</span></span> <span data-ttu-id="37ff5-105">Les contrats de données vous permettent de transférer des données structurées vers des services et à partir de ceux-ci.</span><span class="sxs-lookup"><span data-stu-id="37ff5-105">Data contracts allow you to pass structured data to and from services.</span></span> <span data-ttu-id="37ff5-106">Pour plus d’informations sur les types non marqués, consultez [types sérialisables](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span><span class="sxs-lookup"><span data-stu-id="37ff5-106">For more information about unmarked types, see [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).</span></span>  
  
 <span data-ttu-id="37ff5-107">Cet exemple est basé sur le [prise en main](../../../../docs/framework/wcf/samples/getting-started-sample.md), mais utilise des nombres complexes au lieu de types numériques primitifs.</span><span class="sxs-lookup"><span data-stu-id="37ff5-107">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), but uses complex numbers instead of primitive numeric types.</span></span> <span data-ttu-id="37ff5-108">Elle est également similaire à l’exemple de [contrat de données de base](../../../../docs/framework/wcf/samples/basic-data-contract.md) , <xref:System.Runtime.Serialization.DataContractAttribute> à <xref:System.Runtime.Serialization.DataMemberAttribute> la différence que les attributs et ne sont pas utilisés.</span><span class="sxs-lookup"><span data-stu-id="37ff5-108">It is also similar to the [Basic Data Contract](../../../../docs/framework/wcf/samples/basic-data-contract.md) sample, except that the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes are not used.</span></span>  
  
 <span data-ttu-id="37ff5-109">Le client est une application de console (.exe) et le service est hébergé par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="37ff5-109">The service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="37ff5-110">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="37ff5-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="37ff5-111">La classe `ComplexNumber` est utilisée dans `ServiceContract`.</span><span class="sxs-lookup"><span data-stu-id="37ff5-111">The `ComplexNumber` class is used in the `ServiceContract`.</span></span> <span data-ttu-id="37ff5-112">Le type `ComplexNumber` ne comporte pas les attributs <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute>, comme indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="37ff5-112">The `ComplexNumber` type does not have the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes, as shown in the following sample code.</span></span> <span data-ttu-id="37ff5-113">Par défaut, l'ensemble des propriétés et des champs publics sont sérialisés.</span><span class="sxs-lookup"><span data-stu-id="37ff5-113">By default, all public properties and fields are serialized.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="37ff5-114">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="37ff5-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="37ff5-115">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="37ff5-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="37ff5-116">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="37ff5-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="37ff5-117">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="37ff5-117">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="37ff5-118">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="37ff5-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="37ff5-119">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="37ff5-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="37ff5-120">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et.</span><span class="sxs-lookup"><span data-stu-id="37ff5-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="37ff5-121">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="37ff5-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\POCO`  
  
## <a name="see-also"></a><span data-ttu-id="37ff5-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37ff5-122">See also</span></span>

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- [<span data-ttu-id="37ff5-123">Types sérialisables</span><span class="sxs-lookup"><span data-stu-id="37ff5-123">Serializable Types</span></span>](../../../../docs/framework/wcf/feature-details/serializable-types.md)
