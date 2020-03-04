---
title: Sérialisation de base
ms.date: 03/30/2017
helpviewer_keywords:
- binary serialization, basic serialization
- serialization, basic serialization
ms.assetid: d899d43c-335a-433e-a589-cd187192984f
dev_langs:
- CSharp
ms.openlocfilehash: a2dde9f795dfe31ff6ef821272a0d5e8d20e8b2f
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159947"
---
# <a name="basic-serialization"></a><span data-ttu-id="459e0-102">Sérialisation de base</span><span class="sxs-lookup"><span data-stu-id="459e0-102">Basic serialization</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="459e0-103">La façon la plus simple de rendre une classe sérialisable est de la marquer avec l’attribut <xref:System.SerializableAttribute> comme suit.</span><span class="sxs-lookup"><span data-stu-id="459e0-103">The easiest way to make a class serializable is to mark it with the <xref:System.SerializableAttribute> as follows.</span></span>  
  
```csharp  
[Serializable]  
public class MyObject {  
  public int n1 = 0;  
  public int n2 = 0;  
  public String str = null;  
}  
```  
  
<span data-ttu-id="459e0-104">L’exemple de code suivant illustre comment une instance de cette classe peut être sérialisée dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="459e0-104">The following code example shows how an instance of this class can be serialized to a file.</span></span>  
  
```csharp  
MyObject obj = new MyObject();  
obj.n1 = 1;  
obj.n2 = 24;  
obj.str = "Some String";  
IFormatter formatter = new BinaryFormatter();  
Stream stream = new FileStream("MyFile.bin", FileMode.Create, FileAccess.Write, FileShare.None);  
formatter.Serialize(stream, obj);  
stream.Close();  
```  
  
<span data-ttu-id="459e0-105">Cet exemple utilise un formateur binaire pour effectuer la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="459e0-105">This example uses a binary formatter to do the serialization.</span></span> <span data-ttu-id="459e0-106">Il vous suffit de créer une instance du flux de données et du formateur que vous envisagez d’utiliser, puis d’appeler la méthode **Serialize** sur le formateur.</span><span class="sxs-lookup"><span data-stu-id="459e0-106">All you need to do is create an instance of the stream and the formatter you intend to use, and then call the **Serialize** method on the formatter.</span></span> <span data-ttu-id="459e0-107">Le flux de données et l'objet à sérialiser sont fournis comme paramètres de cet appel.</span><span class="sxs-lookup"><span data-stu-id="459e0-107">The stream and the object to serialize are provided as parameters to this call.</span></span> <span data-ttu-id="459e0-108">Bien que cela n'apparaisse pas explicitement dans cet exemple, toutes les variables membres d'une classe seront sérialisées, même celles marquées comme privées.</span><span class="sxs-lookup"><span data-stu-id="459e0-108">Although it is not explicitly demonstrated in this example, all member variables of a class will be serialized—even variables marked as private.</span></span> <span data-ttu-id="459e0-109">Dans ce cadre, la sérialisation binaire diffère de la classe <xref:System.Xml.Serialization.XmlSerializer>, qui sérialise uniquement des champs publics.</span><span class="sxs-lookup"><span data-stu-id="459e0-109">In this aspect, binary serialization differs from the <xref:System.Xml.Serialization.XmlSerializer> class, which only serializes public fields.</span></span> <span data-ttu-id="459e0-110">Pour plus d’informations sur l’exclusion de variables membres de la sérialisation binaire, consultez [Sérialisation sélective](selective-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="459e0-110">For information on excluding member variables from binary serialization, see [Selective Serialization](selective-serialization.md).</span></span>  
  
<span data-ttu-id="459e0-111">La restauration de l'objet à son état précédent est très facile.</span><span class="sxs-lookup"><span data-stu-id="459e0-111">Restoring the object back to its former state is just as easy.</span></span> <span data-ttu-id="459e0-112">En premier lieu, créez un flux servant à la lecture et un <xref:System.Runtime.Serialization.Formatter>, puis demandez au formateur de désérialiser l’objet.</span><span class="sxs-lookup"><span data-stu-id="459e0-112">First, create a stream for reading and a <xref:System.Runtime.Serialization.Formatter>, and then instruct the formatter to deserialize the object.</span></span> <span data-ttu-id="459e0-113">L'exemple de code suivant illustre cette procédure.</span><span class="sxs-lookup"><span data-stu-id="459e0-113">The code example below shows how this is done.</span></span>  
  
```csharp  
IFormatter formatter = new BinaryFormatter();  
Stream stream = new FileStream("MyFile.bin", FileMode.Open, FileAccess.Read, FileShare.Read);  
MyObject obj = (MyObject) formatter.Deserialize(stream);  
stream.Close();  
  
// Here's the proof.  
Console.WriteLine("n1: {0}", obj.n1);  
Console.WriteLine("n2: {0}", obj.n2);  
Console.WriteLine("str: {0}", obj.str);  
```  
  
<span data-ttu-id="459e0-114">Le <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> utilisé ci-dessus est très efficace et génère un flux d’octets compact.</span><span class="sxs-lookup"><span data-stu-id="459e0-114">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> used above is very efficient and produces a compact byte stream.</span></span> <span data-ttu-id="459e0-115">Ce formateur permet aussi bien de sérialiser que de désérialiser des objets, ce qui en fait l'outil idéal pour sérialiser des objets qui seront désérialisés sur le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="459e0-115">All objects serialized with this formatter can also be deserialized with it, which makes it an ideal tool for serializing objects that will be deserialized on the .NET Framework.</span></span> <span data-ttu-id="459e0-116">Il est important de noter que les constructeurs ne sont pas appelés lorsqu'un objet est désérialisé.</span><span class="sxs-lookup"><span data-stu-id="459e0-116">It is important to note that constructors are not called when an object is deserialized.</span></span> <span data-ttu-id="459e0-117">Pour des raisons de performances, la désérialisation repose sur cette contrainte.</span><span class="sxs-lookup"><span data-stu-id="459e0-117">This constraint is placed on deserialization for performance reasons.</span></span> <span data-ttu-id="459e0-118">Toutefois, cela enfreint les termes de certains contrats habituels que l'exécution passe avec le writer d'objets et les développeurs doivent s'assurer qu'ils comprennent les ramifications lorsqu'ils marquent un objet comme sérialisable.</span><span class="sxs-lookup"><span data-stu-id="459e0-118">However, this violates some of the usual contracts the runtime makes with the object writer, and developers should ensure that they understand the ramifications when marking an object as serializable.</span></span>  
  
<span data-ttu-id="459e0-119">Si la portabilité est une exigence, utilisez plutôt le <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span><span class="sxs-lookup"><span data-stu-id="459e0-119">If portability is a requirement, use the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> instead.</span></span> <span data-ttu-id="459e0-120">Remplacez simplement le **BinaryFormatter** dans le code ci-dessus par **SoapFormatter** et appelez **Serialize** et **Deserialize** comme précédemment.</span><span class="sxs-lookup"><span data-stu-id="459e0-120">Simply replace the **BinaryFormatter** in the code above with **SoapFormatter,** and call **Serialize** and **Deserialize** as before.</span></span> <span data-ttu-id="459e0-121">Ce formateur génère le résultat suivant pour l'exemple utilisé ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="459e0-121">This formatter produces the following output for the example used above.</span></span>  
  
```xml  
<SOAP-ENV:Envelope  
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:SOAP-ENC="http://schemas.xmlsoap.org/soap/encoding/"  
  xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
  SOAP-ENV:encodingStyle=  
  "http://schemas.microsoft.com/soap/encoding/clr/1.0"  
  "http://schemas.xmlsoap.org/soap/encoding/"  
  xmlns:a1="http://schemas.microsoft.com/clr/assem/ToFile">  
  
  <SOAP-ENV:Body>  
    <a1:MyObject id="ref-1">  
      <n1>1</n1>  
      <n2>24</n2>  
      <str id="ref-3">Some String</str>  
    </a1:MyObject>  
  </SOAP-ENV:Body>  
</SOAP-ENV:Envelope>  
```  
  
<span data-ttu-id="459e0-122">Il est important de noter que l’attribut [Serializable](xref:System.SerializableAttribute) ne peut pas être hérité.</span><span class="sxs-lookup"><span data-stu-id="459e0-122">It's important to note that the [Serializable](xref:System.SerializableAttribute) attribute cannot be inherited.</span></span> <span data-ttu-id="459e0-123">Si vous dérivez une nouvelle classe à partir de `MyObject`, elle doit également être marquée avec l'attribut. Sinon, elle ne peut pas être sérialisée.</span><span class="sxs-lookup"><span data-stu-id="459e0-123">If you derive a new class from `MyObject`, the new class must be marked with the attribute as well, or it cannot be serialized.</span></span> <span data-ttu-id="459e0-124">Par exemple, quand vous tentez de sérialiser une instance de la classe ci-dessous, vous obtenez un <xref:System.Runtime.Serialization.SerializationException> vous informant que le type `MyStuff` n’est pas marqué comme sérialisable.</span><span class="sxs-lookup"><span data-stu-id="459e0-124">For example, when you attempt to serialize an instance of the class below, you'll get a <xref:System.Runtime.Serialization.SerializationException> informing you that the `MyStuff` type is not marked as serializable.</span></span>  
  
```csharp  
public class MyStuff : MyObject
{  
  public int n3;  
}  
```  
  
 <span data-ttu-id="459e0-125">L’utilisation de l’attribut [Serializable](xref:System.SerializableAttribute) est pratique, mais comporte des limites comme illustré précédemment.</span><span class="sxs-lookup"><span data-stu-id="459e0-125">Using the [Serializable](xref:System.SerializableAttribute) attribute is convenient, but it has limitations as previously demonstrated.</span></span> <span data-ttu-id="459e0-126">Reportez-vous aux [Indications concernant la sérialisation](serialization-guidelines.md) pour savoir à quel moment il convient de marquer une classe en vue de la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="459e0-126">Refer to the [Serialization Guidelines](serialization-guidelines.md) for information about when you should mark a class for serialization.</span></span> <span data-ttu-id="459e0-127">La sérialisation ne peut pas être ajoutée à une classe une fois que cette dernière a été compilée.</span><span class="sxs-lookup"><span data-stu-id="459e0-127">Serialization cannot be added to a class after it has been compiled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="459e0-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="459e0-128">See also</span></span>

- [<span data-ttu-id="459e0-129">Sérialisation binaire</span><span class="sxs-lookup"><span data-stu-id="459e0-129">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="459e0-130">Sérialisation XML et SOAP</span><span class="sxs-lookup"><span data-stu-id="459e0-130">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
