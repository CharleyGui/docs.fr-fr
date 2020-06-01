---
title: Comment lire des données d’objet à partir d’un fichier XML (C#)
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: e2365d1260d3f6e239f294b2af3399c2fb659575
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241875"
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a><span data-ttu-id="5c451-102">Comment lire des données d’objet à partir d’un fichier XML (C#)</span><span class="sxs-lookup"><span data-stu-id="5c451-102">How to read object data from an XML file (C#)</span></span>
<span data-ttu-id="5c451-103">Cet exemple lit des données d’objet écrites précédemment dans un fichier XML en utilisant la classe <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="5c451-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c451-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="5c451-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="5c451-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="5c451-105">Compiling the Code</span></span>  
<span data-ttu-id="5c451-106">Remplacez le nom du fichier « c:\temp\SerializationOverview.xml » par le nom du fichier qui contient les données sérialisées.</span><span class="sxs-lookup"><span data-stu-id="5c451-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="5c451-107">Pour plus d’informations sur la sérialisation des données, consultez [Comment écrire des données d’objet dans un fichier XML (C#)](./how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="5c451-107">For more information about serializing data, see [How to write object data to an XML file (C#)](./how-to-write-object-data-to-an-xml-file.md).</span></span>
  
 <span data-ttu-id="5c451-108">La classe doit disposer d’un constructeur public sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="5c451-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="5c451-109">Seuls les propriétés et les champs publics sont désérialisés.</span><span class="sxs-lookup"><span data-stu-id="5c451-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="5c451-110">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="5c451-110">Robust Programming</span></span>  
 <span data-ttu-id="5c451-111">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="5c451-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="5c451-112">La classe qui est sérialisée n’a pas de constructeur public sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="5c451-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="5c451-113">Les données du fichier ne représentent pas les données de la classe à désérialiser.</span><span class="sxs-lookup"><span data-stu-id="5c451-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
- <span data-ttu-id="5c451-114">Le fichier n'existe pas (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="5c451-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="5c451-115">Sécurité .NET</span><span class="sxs-lookup"><span data-stu-id="5c451-115">.NET Security</span></span>  
 <span data-ttu-id="5c451-116">Vérifiez toujours les entrées et ne désérialisez jamais les données provenant d’une source non fiable.</span><span class="sxs-lookup"><span data-stu-id="5c451-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="5c451-117">L’objet recréé s’exécute sur un ordinateur local avec les autorisations du code qui l’a désérialisé.</span><span class="sxs-lookup"><span data-stu-id="5c451-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="5c451-118">Vérifiez toutes les entrées avant d'utiliser les données dans votre application.</span><span class="sxs-lookup"><span data-stu-id="5c451-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c451-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5c451-119">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="5c451-120">Comment écrire des données d’objet dans un fichier XML (C#)</span><span class="sxs-lookup"><span data-stu-id="5c451-120">How to write object data to an XML file (C#)</span></span>](./how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="5c451-121">Sérialisation (C#)</span><span class="sxs-lookup"><span data-stu-id="5c451-121">Serialization (C#)</span></span>](./index.md)
- [<span data-ttu-id="5c451-122">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="5c451-122">C# Programming Guide</span></span>](../../index.md)
