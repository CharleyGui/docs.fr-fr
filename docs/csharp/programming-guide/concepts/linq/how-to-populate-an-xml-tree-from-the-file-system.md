---
title: Comment peupler un arbre XML du système de fichiers (C)
ms.date: 07/20/2015
ms.assetid: 2aa2ccac-4a22-47ae-9107-3bb8df232576
ms.openlocfilehash: beb44be1a787fa09b091aa48022dbb5b10c4632b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345781"
---
# <a name="how-to-populate-an-xml-tree-from-the-file-system-c"></a><span data-ttu-id="d355a-102">Comment peupler un arbre XML du système de fichiers (C)</span><span class="sxs-lookup"><span data-stu-id="d355a-102">How to populate an XML tree from the file system (C#)</span></span>
<span data-ttu-id="d355a-103">Une application courante et utile des arborescences XML consiste à les utiliser en tant que banque de données nom/valeur hiérarchique.</span><span class="sxs-lookup"><span data-stu-id="d355a-103">A common and useful application of XML trees is as a hierarchical name/value data store.</span></span> <span data-ttu-id="d355a-104">Vous pouvez remplir une arborescence XML avec des données hiérarchiques, puis les interroger, les transformer et, si nécessaire, les sérialiser.</span><span class="sxs-lookup"><span data-stu-id="d355a-104">You can populate an XML tree with hierarchical data, and then query it, transform it, and if necessary, serialize it.</span></span> <span data-ttu-id="d355a-105">Dans ce scénario, une grande partie de la sémantique spécifique au langage XML, telle que les espaces de noms et le comportement d'espace blanc, n'est pas importante.</span><span class="sxs-lookup"><span data-stu-id="d355a-105">In this usage scenario, many of the XML specific semantics, such as namespaces and white space behavior, are not important.</span></span> <span data-ttu-id="d355a-106">Au lieu de cela, vous utilisez l’arborescence XML en tant que petite base de données hiérarchique en mémoire et à utilisateur unique.</span><span class="sxs-lookup"><span data-stu-id="d355a-106">Instead, you are using the XML tree as a small, in memory, single user hierarchical database.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d355a-107"> Exemple</span><span class="sxs-lookup"><span data-stu-id="d355a-107">Example</span></span>  
 <span data-ttu-id="d355a-108">L’exemple suivant remplit une arborescence XML à partir du système de fichiers à l’aide de la récursivité.</span><span class="sxs-lookup"><span data-stu-id="d355a-108">The following example populates an XML tree from the local file system using recursion.</span></span> <span data-ttu-id="d355a-109">Il interroge ensuite l'arborescence XML et calcule le total de tous les fichiers dans l'arborescence.</span><span class="sxs-lookup"><span data-stu-id="d355a-109">It then queries the tree, calculating the total of the sizes of all files in the tree.</span></span>  
  
```csharp  
class Program  
{  
    static XElement CreateFileSystemXmlTree(string source)  
    {  
        DirectoryInfo di = new DirectoryInfo(source);  
        return new XElement("Dir",  
            new XAttribute("Name", di.Name),  
            from d in Directory.GetDirectories(source)  
            select CreateFileSystemXmlTree(d),  
            from fi in di.GetFiles()  
            select new XElement("File",  
                new XElement("Name", fi.Name),  
                new XElement("Length", fi.Length)  
            )  
        );  
    }  
  
    static void Main(string[] args)  
    {  
        XElement fileSystemTree = CreateFileSystemXmlTree("C:/Tmp");  
        Console.WriteLine(fileSystemTree);  
        Console.WriteLine("------");  
        long totalFileSize =  
            (from f in fileSystemTree.Descendants("File")  
             select (long)f.Element("Length")).Sum();  
        Console.WriteLine("Total File Size:{0}", totalFileSize);  
    }  
}  
```  
  
 <span data-ttu-id="d355a-110">Cet exemple produit une sortie semblable à la suivante :</span><span class="sxs-lookup"><span data-stu-id="d355a-110">This example produces output similar to the following:</span></span>  
  
```xml  
<Dir Name="Tmp">  
  <Dir Name="ConsoleApplication1">  
    <Dir Name="bin">  
      <Dir Name="Debug">  
        <File>  
          <Name>ConsoleApplication1.exe</Name>  
          <Length>4608</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.pdb</Name>  
          <Length>11776</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.vshost.exe</Name>  
          <Length>9568</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.vshost.exe.manifest</Name>  
          <Length>473</Length>  
        </File>  
      </Dir>  
    </Dir>  
    <Dir Name="obj">  
      <Dir Name="Debug">  
        <Dir Name="TempPE" />  
        <File>  
          <Name>ConsoleApplication1.csproj.FileListAbsolute.txt</Name>  
          <Length>322</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.exe</Name>  
          <Length>4608</Length>  
        </File>  
        <File>  
          <Name>ConsoleApplication1.pdb</Name>  
          <Length>11776</Length>  
        </File>  
      </Dir>  
    </Dir>  
    <Dir Name="Properties">  
      <File>  
        <Name>AssemblyInfo.cs</Name>  
        <Length>1454</Length>  
      </File>  
    </Dir>  
    <File>  
      <Name>ConsoleApplication1.csproj</Name>  
      <Length>2546</Length>  
    </File>  
    <File>  
      <Name>ConsoleApplication1.sln</Name>  
      <Length>937</Length>  
    </File>  
    <File>  
      <Name>ConsoleApplication1.suo</Name>  
      <Length>10752</Length>  
    </File>  
    <File>  
      <Name>Program.cs</Name>  
      <Length>269</Length>  
    </File>  
  </Dir>  
</Dir>  
------  
Total File Size:59089  
```  
