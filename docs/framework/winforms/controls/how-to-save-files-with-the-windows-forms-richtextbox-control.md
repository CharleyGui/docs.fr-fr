---
title: 'Procédure : enregistrer des fichiers avec le contrôle RichTextBox Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- saving files
- RTF files [Windows Forms], saving in RichTextBox control
- examples [Windows Forms], text boxes
- saving files [Windows Forms], RichTextBox control
- files [Windows Forms], saving with RichTextBox control
- RichTextBox control [Windows Forms], saving files
- .rtf files [Windows Forms], saving in RichTextBox control
- text files [Windows Forms], saving from RichTextBox control
ms.assetid: 4a58ec19-84d1-4383-9110-298c06adcfca
ms.openlocfilehash: 9a4f5a98c9fea9658d9d9a400faa773b78a12f3a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638320"
---
# <a name="how-to-save-files-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="a7c75-102">Procédure : enregistrer des fichiers avec le contrôle RichTextBox Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7c75-102">How to: Save Files with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="a7c75-103">Les formulaires Windows <xref:System.Windows.Forms.RichTextBox> contrôle peut écrire les informations affichées dans un des formats suivants :</span><span class="sxs-lookup"><span data-stu-id="a7c75-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can write the information it displays in one of several formats:</span></span>  
  
- <span data-ttu-id="a7c75-104">Texte brut</span><span class="sxs-lookup"><span data-stu-id="a7c75-104">Plain text</span></span>  
  
- <span data-ttu-id="a7c75-105">Texte brut Unicode</span><span class="sxs-lookup"><span data-stu-id="a7c75-105">Unicode plain text</span></span>  
  
- <span data-ttu-id="a7c75-106">Format de texte enrichi (RTF)</span><span class="sxs-lookup"><span data-stu-id="a7c75-106">Rich-Text Format (RTF)</span></span>  
  
- <span data-ttu-id="a7c75-107">RTF avec des espaces à la place des objets OLE</span><span class="sxs-lookup"><span data-stu-id="a7c75-107">RTF with spaces in place of OLE objects</span></span>  
  
- <span data-ttu-id="a7c75-108">Texte brut avec une représentation textuelle des objets OLE</span><span class="sxs-lookup"><span data-stu-id="a7c75-108">Plain text with a textual representation of OLE objects</span></span>  
  
 <span data-ttu-id="a7c75-109">Pour enregistrer un fichier, appelez le <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="a7c75-109">To save a file, call the <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> method.</span></span> <span data-ttu-id="a7c75-110">Vous pouvez également utiliser le **SaveFile** méthode pour enregistrer les données dans un flux.</span><span class="sxs-lookup"><span data-stu-id="a7c75-110">You can also use the **SaveFile** method to save data to a stream.</span></span> <span data-ttu-id="a7c75-111">Pour plus d'informations, consultez <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span><span class="sxs-lookup"><span data-stu-id="a7c75-111">For more information, see <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span></span>  
  
### <a name="to-save-the-contents-of-the-control-to-a-file"></a><span data-ttu-id="a7c75-112">Pour enregistrer le contenu du contrôle dans un fichier</span><span class="sxs-lookup"><span data-stu-id="a7c75-112">To save the contents of the control to a file</span></span>  
  
1. <span data-ttu-id="a7c75-113">Déterminer le chemin d’accès du fichier à enregistrer.</span><span class="sxs-lookup"><span data-stu-id="a7c75-113">Determine the path of the file to be saved.</span></span>  
  
     <span data-ttu-id="a7c75-114">Pour ce faire, dans une application réelle, vous utiliseriez généralement le <xref:System.Windows.Forms.SaveFileDialog> composant.</span><span class="sxs-lookup"><span data-stu-id="a7c75-114">To do this in a real-world application, you would typically use the <xref:System.Windows.Forms.SaveFileDialog> component.</span></span> <span data-ttu-id="a7c75-115">Pour une vue d’ensemble, consultez [vue d’ensemble du composant SaveFileDialog](savefiledialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a7c75-115">For an overview, see [SaveFileDialog Component Overview](savefiledialog-component-overview-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="a7c75-116">Appelez le <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> méthode de la <xref:System.Windows.Forms.RichTextBox> contrôle, en spécifiant le fichier à enregistrer et éventuellement un type de fichier.</span><span class="sxs-lookup"><span data-stu-id="a7c75-116">Call the <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> method of the <xref:System.Windows.Forms.RichTextBox> control, specifying the file to save and optionally a file type.</span></span> <span data-ttu-id="a7c75-117">Si vous appelez la méthode avec un nom de fichier comme seul argument, le fichier sera enregistré au format RTF.</span><span class="sxs-lookup"><span data-stu-id="a7c75-117">If you call the method with a file name as its only argument, the file will be saved as RTF.</span></span> <span data-ttu-id="a7c75-118">Pour spécifier un autre type de fichier, appelez la méthode en spécifiant une valeur pour l’énumération <xref:System.Windows.Forms.RichTextBoxStreamType> comme deuxième argument.</span><span class="sxs-lookup"><span data-stu-id="a7c75-118">To specify another file type, call the method with a value of the <xref:System.Windows.Forms.RichTextBoxStreamType> enumeration as its second argument.</span></span>  
  
     <span data-ttu-id="a7c75-119">Dans l’exemple ci-dessous, le chemin d’accès défini pour l’emplacement du fichier de texte enrichi est la **Mes Documents** dossier.</span><span class="sxs-lookup"><span data-stu-id="a7c75-119">In the example below, the path set for the location of the rich-text file is the **My Documents** folder.</span></span> <span data-ttu-id="a7c75-120">Cet emplacement est utilisé, car vous pouvez supposer que la plupart des ordinateurs exécutant le système d’exploitation Windows incluent ce dossier.</span><span class="sxs-lookup"><span data-stu-id="a7c75-120">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="a7c75-121">Choix de cet emplacement permet également aux utilisateurs avec des niveaux d’accès système minimal exécuter en toute sécurité de l’application.</span><span class="sxs-lookup"><span data-stu-id="a7c75-121">Choosing this location also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="a7c75-122">L’exemple suivant suppose un formulaire avec un <xref:System.Windows.Forms.RichTextBox> contrôle déjà ajouté.</span><span class="sxs-lookup"><span data-stu-id="a7c75-122">The example below assumes a form with a <xref:System.Windows.Forms.RichTextBox> control already added.</span></span>  
  
    ```vb  
    Public Sub SaveFile()  
       ' You should replace the bold file name in the   
       ' sample below with a file name of your own choosing.  
       RichTextBox1.SaveFile(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Testdoc.rtf", _  
          RichTextBoxStreamType.RichNoOleObjs)  
    End Sub  
    ```  
  
    ```csharp  
    public void SaveFile()  
    {  
       // You should replace the bold file name in the   
       // sample below with a file name of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       richTextBox1.SaveFile(System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Testdoc.rtf",  
          RichTextBoxStreamType.RichNoOleObjs);  
    }  
    ```  
  
    ```cpp  
    public:  
       void SaveFile()  
       {  
          // You should replace the bold file name in the   
          // sample below with a file name of your own choosing.  
          richTextBox1->SaveFile(String::Concat  
             (System::Environment::GetFolderPath  
             (System::Environment::SpecialFolder::Personal),  
             "\\Testdoc.rtf"), RichTextBoxStreamType::RichNoOleObjs);  
       }  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="a7c75-123">Cet exemple crée un fichier s’il n’existe pas déjà.</span><span class="sxs-lookup"><span data-stu-id="a7c75-123">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="a7c75-124">Si une application a besoin créer un fichier, cette application a besoin d’accéder de créer pour le dossier.</span><span class="sxs-lookup"><span data-stu-id="a7c75-124">If an application needs to create a file, that application needs Create access for the folder.</span></span> <span data-ttu-id="a7c75-125">Les autorisations sont définies à l’aide des listes de contrôle d’accès.</span><span class="sxs-lookup"><span data-stu-id="a7c75-125">Permissions are set using access control lists.</span></span> <span data-ttu-id="a7c75-126">Si le fichier existe déjà, l’application doit uniquement un accès en écriture, un privilège inférieur.</span><span class="sxs-lookup"><span data-stu-id="a7c75-126">If the file already exists, the application needs only Write access, a lesser privilege.</span></span> <span data-ttu-id="a7c75-127">Si possible, il est plus sûr de créer le fichier pendant le déploiement et uniquement accorder l’accès en lecture à un seul fichier, au lieu de créer l’accès pour un dossier.</span><span class="sxs-lookup"><span data-stu-id="a7c75-127">Where possible, it is more secure to create the file during deployment, and only grant Read access to a single file, rather than Create access for a folder.</span></span> <span data-ttu-id="a7c75-128">En outre, il est plus sûr d’écrire les données dans des dossiers utilisateur que dans le dossier racine ou le dossier Program Files.</span><span class="sxs-lookup"><span data-stu-id="a7c75-128">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7c75-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7c75-129">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="a7c75-130">RichTextBox, contrôle</span><span class="sxs-lookup"><span data-stu-id="a7c75-130">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="a7c75-131">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a7c75-131">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
