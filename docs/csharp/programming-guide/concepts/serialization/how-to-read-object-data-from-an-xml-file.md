---
title: Comment lire les données d’objets à partir d’un fichier XML (C)
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: 18428cbe2f2d3b9434a77ee4d063ceabbba6bcb8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167816"
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a><span data-ttu-id="e0bee-102">Comment lire les données d’objets à partir d’un fichier XML (C)</span><span class="sxs-lookup"><span data-stu-id="e0bee-102">How to read object data from an XML file (C#)</span></span>
<span data-ttu-id="e0bee-103">Cet exemple lit des données d’objet écrites précédemment dans un fichier XML en utilisant la classe <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="e0bee-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0bee-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="e0bee-104">Example</span></span>  
  
```csharp  
public class Book  
{  
    public String title;  
}
  
public void ReadXML()  
{  
    // First write something so that there is something to read ...  
    var b = new Book { title = "Serialization Overview" };  
    var writer = new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    var wfile = new System.IO.StreamWriter(@"c:\temp\SerializationOverview.xml");  
    writer.Serialize(wfile, b);  
    wfile.Close();  
  
    // Now we can read the serialized book ...  
    System.Xml.Serialization.XmlSerializer reader =
        new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    System.IO.StreamReader file = new System.IO.StreamReader(  
        @"c:\temp\SerializationOverview.xml");  
    Book overview =  (Book)reader.Deserialize(file);  
    file.Close();  
  
    Console.WriteLine(overview.title);  
  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e0bee-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="e0bee-105">Compiling the Code</span></span>  
<span data-ttu-id="e0bee-106">Remplacez le nom du fichier « c:\temp\SerializationOverview.xml » par le nom du fichier qui contient les données sérialisées.</span><span class="sxs-lookup"><span data-stu-id="e0bee-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="e0bee-107">Pour plus d’informations sur la sérialisation des données, voir [Comment écrire des données d’objets à un fichier XML (C)](./how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="e0bee-107">For more information about serializing data, see [How to write object data to an XML file (C#)](./how-to-write-object-data-to-an-xml-file.md).</span></span>
  
 <span data-ttu-id="e0bee-108">La classe doit disposer d’un constructeur public sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="e0bee-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="e0bee-109">Seuls les propriétés et les champs publics sont désérialisés.</span><span class="sxs-lookup"><span data-stu-id="e0bee-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e0bee-110">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="e0bee-110">Robust Programming</span></span>  
 <span data-ttu-id="e0bee-111">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="e0bee-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="e0bee-112">La classe qui est sérialisée n’a pas de constructeur public sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="e0bee-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="e0bee-113">Les données du fichier ne représentent pas les données de la classe à désérialiser.</span><span class="sxs-lookup"><span data-stu-id="e0bee-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
- <span data-ttu-id="e0bee-114">Le fichier n'existe pas (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="e0bee-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="e0bee-115">Sécurité du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e0bee-115">.NET Framework Security</span></span>  
 <span data-ttu-id="e0bee-116">Vérifiez toujours les entrées et ne désérialisez jamais les données provenant d’une source non fiable.</span><span class="sxs-lookup"><span data-stu-id="e0bee-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="e0bee-117">L’objet recréé s’exécute sur un ordinateur local avec les autorisations du code qui l’a désérialisé.</span><span class="sxs-lookup"><span data-stu-id="e0bee-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="e0bee-118">Vérifiez toutes les entrées avant d'utiliser les données dans votre application.</span><span class="sxs-lookup"><span data-stu-id="e0bee-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0bee-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0bee-119">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="e0bee-120">Comment écrire des données d’objet à un fichier XML (C)</span><span class="sxs-lookup"><span data-stu-id="e0bee-120">How to write object data to an XML file (C#)</span></span>](./how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="e0bee-121">Sérialisation (C#)</span><span class="sxs-lookup"><span data-stu-id="e0bee-121">Serialization (C#)</span></span>](./index.md)
- [<span data-ttu-id="e0bee-122">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="e0bee-122">C# Programming Guide</span></span>](../../index.md)
