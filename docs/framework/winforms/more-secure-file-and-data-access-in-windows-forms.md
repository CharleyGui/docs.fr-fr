---
title: Accès plus sécurisé aux fichiers et aux données
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [Windows Forms], file access
- registry [Windows Forms]
- data access [Windows Forms]
- database access (Windows Forms security)
- data [Windows Forms], secure access
- file access [Windows Forms]
- security [Windows Forms], data access
ms.assetid: 3cd3e55b-2f5e-40dd-835d-f50f7ce08967
ms.openlocfilehash: 49ba1919f68f35e9d72b012540b785e05c307c39
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743751"
---
# <a name="more-secure-file-and-data-access-in-windows-forms"></a><span data-ttu-id="ce0e5-102">Accès plus sécurisé aux fichiers et aux données dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ce0e5-102">More Secure File and Data Access in Windows Forms</span></span>
<span data-ttu-id="ce0e5-103">Le .NET Framework utilise des autorisations pour protéger les ressources et les données.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-103">The .NET Framework uses permissions to help protect resources and data.</span></span> <span data-ttu-id="ce0e5-104">L'emplacement où votre application peut lire ou écrire des données dépend des autorisations qui lui sont accordées.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-104">Where your application can read or write data depends on the permissions granted to the application.</span></span> <span data-ttu-id="ce0e5-105">Quand votre application s'exécute dans un environnement de confiance partielle, vous n'avez peut-être pas accès à vos données ou vous devrez peut-être modifier la manière dont vous accédez aux données.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-105">When your application runs in a partial trust environment, you might not have access to your data or you might have to change the way you access the data.</span></span>  
  
 <span data-ttu-id="ce0e5-106">Quand vous rencontrez une restriction de sécurité, vous avez deux options : déclarer l'autorisation (en supposant qu'elle a été accordée à votre application) ou utiliser une version de la fonctionnalité écrite pour fonctionner en mode de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-106">When you encounter a security restriction, you have two options: assert the permission (assuming it has been granted to your application), or use a version of the feature written to work in partial trust.</span></span> <span data-ttu-id="ce0e5-107">Les sections suivantes décrivent comment gérer l'accès aux fichiers, aux bases de données et au Registre à partir d'applications qui s'exécutent dans un environnement de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-107">The following sections discuss how to work with file, database, and registry access from applications that are running in a partial trust environment.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce0e5-108">Par défaut, les outils qui génèrent des déploiements ClickOnce ont par défaut ces déploiements qui demandent une confiance totale à partir des ordinateurs sur lesquels ils s’exécutent.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-108">By default, tools that generate ClickOnce deployments default these deployments to requesting Full Trust from the computers on which they run.</span></span> <span data-ttu-id="ce0e5-109">Si vous souhaitez bénéficier des avantages de sécurité supplémentaires liés à l’exécution en mode de confiance partielle, vous devez modifier cette valeur par défaut dans Visual Studio ou dans l’un des outils de SDK Windows (Mage. exe ou MageUI. exe).</span><span class="sxs-lookup"><span data-stu-id="ce0e5-109">If you decide you want the added security benefits of running in partial trust, you must change this default in either Visual Studio or one of the Windows SDK tools (Mage.exe or MageUI.exe).</span></span> <span data-ttu-id="ce0e5-110">Pour plus d’informations sur la sécurité Windows Forms et sur la façon de déterminer le niveau de confiance approprié pour votre application, consultez [vue d’ensemble de la sécurité dans Windows Forms](security-in-windows-forms-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ce0e5-110">For more information about Windows Forms security, and on how to determine the appropriate trust level for your application, see [Security in Windows Forms Overview](security-in-windows-forms-overview.md).</span></span>  
  
## <a name="file-access"></a><span data-ttu-id="ce0e5-111">Accès aux fichiers</span><span class="sxs-lookup"><span data-stu-id="ce0e5-111">File Access</span></span>  
 <span data-ttu-id="ce0e5-112">La classe <xref:System.Security.Permissions.FileIOPermission> contrôle l’accès aux fichiers et aux dossiers dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-112">The <xref:System.Security.Permissions.FileIOPermission> class controls file and folder access in the .NET Framework.</span></span> <span data-ttu-id="ce0e5-113">Par défaut, le système de sécurité n'accorde pas <xref:System.Security.Permissions.FileIOPermission> aux environnements de confiance partielle tels que les zones Intranet local et Internet.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-113">By default, the security system does not grant the <xref:System.Security.Permissions.FileIOPermission> to partial trust environments such as the local intranet and Internet zones.</span></span> <span data-ttu-id="ce0e5-114">Cependant, une application qui nécessite l'accès aux fichiers peut quand même fonctionner dans ces environnements si vous modifiez la conception de votre application ou si vous utilisez des méthodes différentes pour accéder aux fichiers.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-114">However, an application that requires file access can still function in these environments if you modify the design of your application or use different methods to access files.</span></span> <span data-ttu-id="ce0e5-115">Par défaut, la zone Intranet local est autorisée à accéder au même site et au même répertoire, à se reconnecter au site de son origine et à lire à partir de son répertoire d'installation.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-115">By default, the local intranet zone is granted the right to have same site access and same directory access, to connect back to the site of its origin, and to read from its installation directory.</span></span> <span data-ttu-id="ce0e5-116">Par défaut, la zone Internet est autorisée uniquement à se reconnecter au site de son origine.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-116">By default, the Internet zone, is only granted the right to connect back to the site of its origin.</span></span>  
  
### <a name="user-specified-files"></a><span data-ttu-id="ce0e5-117">Fichiers spécifiés par l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="ce0e5-117">User-Specified Files</span></span>  
 <span data-ttu-id="ce0e5-118">L'une des façons de gérer le fait de ne pas avoir l'autorisation d'accès aux fichiers consiste à inviter l'utilisateur à fournir des informations de fichiers spécifiques à l'aide de la classe <xref:System.Windows.Forms.OpenFileDialog> ou <xref:System.Windows.Forms.SaveFileDialog>.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-118">One way to deal with not having file access permission is to prompt the user to provide specific file information by using the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog> class.</span></span> <span data-ttu-id="ce0e5-119">Cette interaction utilisateur permet de fournir une garantie que l'application ne peut pas remplacer des fichiers importants ou charger des fichiers privés à des fins malveillantes.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-119">This user interaction helps provide some assurance that the application cannot maliciously load private files or overwrite important files.</span></span> <span data-ttu-id="ce0e5-120">Les méthodes <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> et <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> fournissent un accès en lecture et en écriture aux fichiers en ouvrant le flux de fichier pour le fichier spécifié par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-120">The <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> and <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> methods provide read and write file access by opening the file stream for the file that the user specified.</span></span> <span data-ttu-id="ce0e5-121">Ces méthodes aident aussi à protéger les fichiers de l’utilisateur en masquant leur chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-121">The methods also help protect the user's file by obscuring the file's path.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce0e5-122">Ces autorisations diffèrent selon que votre application est dans la zone Internet ou Intranet.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-122">These permissions differ depending on whether your application is in the Internet zone or Intranet zone.</span></span> <span data-ttu-id="ce0e5-123">Les applications de la zone Internet peuvent uniquement utiliser <xref:System.Windows.Forms.OpenFileDialog>, alors que les applications de la zone Intranet ont une autorisation Boîte de dialogue Fichier illimitée.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-123">Internet zone applications can only use the <xref:System.Windows.Forms.OpenFileDialog>, whereas Intranet applications have unrestricted file dialog permission.</span></span>  
  
 <span data-ttu-id="ce0e5-124">La classe <xref:System.Security.Permissions.FileDialogPermission> spécifie le type de boîte de dialogue Fichier que votre application peut utiliser.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-124">The <xref:System.Security.Permissions.FileDialogPermission> class specifies what type of file dialog box your application can use.</span></span> <span data-ttu-id="ce0e5-125">Le tableau suivant indique la valeur que vous devez avoir pour utiliser chaque classe <xref:System.Windows.Forms.FileDialog>.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-125">The following table shows the value you must have to use each <xref:System.Windows.Forms.FileDialog> class.</span></span>  
  
|<span data-ttu-id="ce0e5-126">Class</span><span class="sxs-lookup"><span data-stu-id="ce0e5-126">Class</span></span>|<span data-ttu-id="ce0e5-127">Valeur d'accès nécessaire</span><span class="sxs-lookup"><span data-stu-id="ce0e5-127">Required access value</span></span>|  
|-----------|---------------------------|  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Open>|  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Save>|  
  
> [!NOTE]
> <span data-ttu-id="ce0e5-128">L'autorisation spécifique n'est pas demandée tant que la méthode <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> n'est pas appelée.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-128">The specific permission is not requested until the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method is actually called.</span></span>  
  
 <span data-ttu-id="ce0e5-129">L'autorisation d'afficher une boîte de dialogue Fichier n'accorde pas à votre application un accès total à tous les membres des classes <xref:System.Windows.Forms.FileDialog>, <xref:System.Windows.Forms.OpenFileDialog> et <xref:System.Windows.Forms.SaveFileDialog>.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-129">Permission to display a file dialog box does not grant your application full access to all members of the <xref:System.Windows.Forms.FileDialog>, <xref:System.Windows.Forms.OpenFileDialog>, and <xref:System.Windows.Forms.SaveFileDialog> classes.</span></span> <span data-ttu-id="ce0e5-130">Pour connaître les autorisations requises pour appeler chaque méthode, consultez la rubrique de référence pour cette méthode dans la documentation de la bibliothèque de classes .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-130">For the exact permissions that are required to call each method, see the reference topic for that method in the .NET Framework class library documentation.</span></span>  
  
 <span data-ttu-id="ce0e5-131">L'exemple de code suivant utilise la méthode <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> pour ouvrir un fichier spécifié par l'utilisateur dans un contrôle <xref:System.Windows.Forms.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-131">The following code example uses the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to open a user-specified file into a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="ce0e5-132">L'exemple exige <xref:System.Security.Permissions.FileDialogPermission> et la valeur d'énumération <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> associée.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-132">The example requires <xref:System.Security.Permissions.FileDialogPermission> and the associated <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> enumeration value.</span></span> <span data-ttu-id="ce0e5-133">Il illustre comment gérer <xref:System.Security.SecurityException> pour déterminer si la fonctionnalité d’enregistrement doit être désactivée.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-133">The example demonstrates how to handle the <xref:System.Security.SecurityException> to determine whether the save feature should be disabled.</span></span> <span data-ttu-id="ce0e5-134">Cet exemple exige que votre <xref:System.Windows.Forms.Form> ait un contrôle <xref:System.Windows.Forms.Button> nommé `ButtonOpen` et un contrôle <xref:System.Windows.Forms.RichTextBox> nommé `RtfBoxMain`.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-134">This example requires that your <xref:System.Windows.Forms.Form> has a <xref:System.Windows.Forms.Button> control named `ButtonOpen`, and a <xref:System.Windows.Forms.RichTextBox> control named `RtfBoxMain`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ce0e5-135">La logique de programmation pour la fonctionnalité d’enregistrement n’est pas illustrée dans l’exemple.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-135">The programming logic for the save feature is not shown in the example.</span></span>  
  
```vb  
Private Sub ButtonOpen_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles ButtonOpen.Click   
  
    Dim editingFileName as String = ""  
    Dim saveAllowed As Boolean = True  
  
    ' Displays the OpenFileDialog.  
    If (OpenFileDialog1.ShowDialog() = DialogResult.OK) Then  
        Dim userStream as System.IO.Stream  
        Try   
            ' Opens the file stream for the file selected by the user.  
            userStream =OpenFileDialog1.OpenFile()   
            Me.RtfBoxMain.LoadFile(userStream, _  
                RichTextBoxStreamType.PlainText)  
        Finally  
            userStream.Close()  
        End Try  
  
        ' Tries to get the file name selected by the user.  
        ' Failure means that the application does not have  
        ' unrestricted permission to the file.  
        Try   
            editingFileName = OpenFileDialog1.FileName  
        Catch ex As Exception  
            If TypeOf ex Is System.Security.SecurityException Then   
                ' The application does not have unrestricted permission   
                ' to the file so the save feature will be disabled.  
                saveAllowed = False   
            Else   
                Throw ex  
            End If  
        End Try  
    End If  
End Sub  
```  
  
```csharp  
private void ButtonOpen_Click(object sender, System.EventArgs e)   
{  
    String editingFileName = "";  
    Boolean saveAllowed = true;  
  
    // Displays the OpenFileDialog.  
    if (openFileDialog1.ShowDialog() == DialogResult.OK)   
    {  
        // Opens the file stream for the file selected by the user.  
        using (System.IO.Stream userStream = openFileDialog1.OpenFile())   
        {  
            this.RtfBoxMain.LoadFile(userStream,  
                RichTextBoxStreamType.PlainText);  
            userStream.Close();  
        }  
  
        // Tries to get the file name selected by the user.  
        // Failure means that the application does not have  
        // unrestricted permission to the file.  
        try   
        {  
            editingFileName = openFileDialog1.FileName;  
        }   
        catch (Exception ex)   
        {  
            if (ex is System.Security.SecurityException)   
            {  
                // The application does not have unrestricted permission   
                // to the file so the save feature will be disabled.  
                saveAllowed = false;   
            }   
            else   
            {  
                throw ex;  
            }  
        }  
    }  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="ce0e5-136">Dans Visual C#, veillez à ajouter du code pour activer le gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-136">In Visual C#, ensure that you add code to enable the event handler.</span></span> <span data-ttu-id="ce0e5-137">En utilisant le code de l'exemple précédent, le code suivant montre comment activer le gestionnaire d'événements.`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`</span><span class="sxs-lookup"><span data-stu-id="ce0e5-137">By using the code from the previous example, the following code shows how to enable the event handler.`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`</span></span>  
  
### <a name="other-files"></a><span data-ttu-id="ce0e5-138">Autres fichiers</span><span class="sxs-lookup"><span data-stu-id="ce0e5-138">Other Files</span></span>  
 <span data-ttu-id="ce0e5-139">Vous devrez parfois lire ou écrire dans des fichiers que l'utilisateur ne spécifie pas, par exemple quand vous devrez conserver les paramètres d'application.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-139">Sometimes you will need to read or write to files that the user does not specify, such as when you must persist application settings.</span></span> <span data-ttu-id="ce0e5-140">Dans les zones Intranet local et Internet, votre application ne sera pas autorisée à stocker des données dans un fichier local.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-140">In the local intranet and Internet zones, your application will not have permission to store data in a local file.</span></span> <span data-ttu-id="ce0e5-141">Toutefois, elle pourra stocker des données dans un stockage isolé.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-141">However, your application will be able to store data in isolated storage.</span></span> <span data-ttu-id="ce0e5-142">Le stockage isolé est un compartiment de données abstrait (et non un emplacement de stockage spécifique) composé d'au moins un fichier de stockage isolé, appelé magasin, contenant les emplacements de répertoire réels où sont stockées les données.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-142">Isolated storage is an abstract data compartment (not a specific storage location) that contains one or more isolated storage files, called stores, that contain the actual directory locations where data is stored.</span></span> <span data-ttu-id="ce0e5-143">Les autorisations d'accès aux fichiers telles que <xref:System.Security.Permissions.FileIOPermission> ne sont pas nécessaires. Au lieu de cela, la classe <xref:System.Security.Permissions.IsolatedStoragePermission> contrôle les autorisations pour le stockage isolé.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-143">File access permissions like <xref:System.Security.Permissions.FileIOPermission> are not required; instead, the <xref:System.Security.Permissions.IsolatedStoragePermission> class controls the permissions for isolated storage.</span></span> <span data-ttu-id="ce0e5-144">Par défaut, les applications qui s'exécutent dans les zones Intranet local et Internet peuvent stocker des données à l'aide du stockage isolé. Toutefois, des paramètres tels que les quotas de disque peuvent varier.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-144">By default, applications that are running in the local intranet and Internet zones can store data using isolated storage; however, settings like disk quota can vary.</span></span> <span data-ttu-id="ce0e5-145">Pour plus d’informations sur le stockage isolé, consultez [stockage isolé](../../standard/io/isolated-storage.md).</span><span class="sxs-lookup"><span data-stu-id="ce0e5-145">For more information about isolated storage, see [Isolated Storage](../../standard/io/isolated-storage.md).</span></span>  
  
 <span data-ttu-id="ce0e5-146">L'exemple suivant utilise le stockage isolé pour écrire des données dans un fichier situé dans un magasin.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-146">The following example uses isolated storage to write data to a file located in a store.</span></span> <span data-ttu-id="ce0e5-147">Cet exemple nécessite <xref:System.Security.Permissions.IsolatedStorageFilePermission> et la valeur d'énumération <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser>.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-147">The example requires <xref:System.Security.Permissions.IsolatedStorageFilePermission> and the <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser> enumeration value.</span></span> <span data-ttu-id="ce0e5-148">Il illustre comment lire et écrire certaines valeurs de propriétés du contrôle <xref:System.Windows.Forms.Button> dans un fichier dans du stockage isolé.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-148">The example demonstrates reading and writing certain property values of the <xref:System.Windows.Forms.Button> control to a file in isolated storage.</span></span> <span data-ttu-id="ce0e5-149">La fonction `Read` est appelée après le démarrage de l'application et la fonction `Write` est appelée avant la fin de l'application.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-149">The `Read` function would be called after the application starts and the `Write` function would be called before the application ends.</span></span> <span data-ttu-id="ce0e5-150">L’exemple requiert que les fonctions `Read` et `Write` existent en tant que membres d’un <xref:System.Windows.Forms.Form> qui contient un contrôle <xref:System.Windows.Forms.Button> nommé `MainButton`.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-150">The example requires that the `Read` and `Write` functions exist as members of a <xref:System.Windows.Forms.Form> that contains a <xref:System.Windows.Forms.Button> control named `MainButton`.</span></span>  
  
```vb  
' Reads the button options from the isolated storage. Uses Default values   
' for the button if the options file does not exist.  
Public Sub Read()   
    Dim isoStore As System.IO.IsolatedStorage.IsolatedStorageFile = _  
        System.IO.IsolatedStorage.IsolatedStorageFile. _   
        GetUserStoreForDomain()  
  
    Dim filename As String = "options.txt"  
    Try  
        ' Checks to see if the options.txt file exists.  
        If (isoStore.GetFileNames(filename).GetLength(0) <> 0) Then  
  
            ' Opens the file because it exists.  
            Dim isos As New System.IO.IsolatedStorage.IsolatedStorageFileStream _   
                 (filename, IO.FileMode.Open,isoStore)  
            Dim reader as System.IO.StreamReader  
            Try   
                reader = new System.IO.StreamReader(isos)  
  
                ' Reads the values stored.  
                Dim converter As System.ComponentModel.TypeConverter  
                converter = System.ComponentModel.TypeDescriptor.GetConverter _   
                    (GetType(Color))  
  
                Me.MainButton.BackColor = _   
                        CType(converter.ConvertFromString _   
                         (reader.ReadLine()), Color)  
                me.MainButton.ForeColor = _  
                        CType(converter.ConvertFromString _   
                         (reader.ReadLine()), Color)  
  
                converter = System.ComponentModel.TypeDescriptor.GetConverter _   
                    (GetType(Font))  
                me.MainButton.Font = _  
                        CType(converter.ConvertFromString _   
                         (reader.ReadLine()), Font)  
  
            Catch ex As Exception  
                Debug.WriteLine("Cannot read options " + _  
                    ex.ToString())  
            Finally  
                reader.Close()  
            End Try  
        End If  
  
    Catch ex As Exception  
        Debug.WriteLine("Cannot read options " + ex.ToString())  
    End Try  
End Sub  
  
' Writes the button options to the isolated storage.  
Public Sub Write()   
    Dim isoStore As System.IO.IsolatedStorage.IsolatedStorageFile = _  
        System.IO.IsolatedStorage.IsolatedStorageFile. _   
        GetUserStoreForDomain()  
  
    Dim filename As String = "options.txt"  
    Try   
        ' Checks if the file exists, and if it does, tries to delete it.  
        If (isoStore.GetFileNames(filename).GetLength(0) <> 0) Then  
            isoStore.DeleteFile(filename)  
        End If  
    Catch ex As Exception  
        Debug.WriteLine("Cannot delete file " + ex.ToString())  
    End Try  
  
    ' Creates the options.txt file and writes the button options to it.  
    Dim writer as System.IO.StreamWriter  
    Try   
        Dim isos As New System.IO.IsolatedStorage.IsolatedStorageFileStream _   
             (filename, IO.FileMode.CreateNew, isoStore)  
  
        writer = New System.IO.StreamWriter(isos)  
        Dim converter As System.ComponentModel.TypeConverter  
  
        converter = System.ComponentModel.TypeDescriptor.GetConverter _   
           (GetType(Color))  
        writer.WriteLine(converter.ConvertToString( _  
            Me.MainButton.BackColor))  
        writer.WriteLine(converter.ConvertToString( _  
            Me.MainButton.ForeColor))  
  
        converter = System.ComponentModel TypeDescriptor.GetConverter _   
           (GetType(Font))  
        writer.WriteLine(converter.ConvertToString( _  
            Me.MainButton.Font))  
  
    Catch ex as Exception  
        Debug.WriteLine("Cannot write options " + ex.ToString())  
  
    Finally  
        writer.Close()  
    End Try  
End Sub  
```  
  
```csharp  
// Reads the button options from the isolated storage. Uses default values   
// for the button if the options file does not exist.  
public void Read()   
{  
    System.IO.IsolatedStorage.IsolatedStorageFile isoStore =   
        System.IO.IsolatedStorage.IsolatedStorageFile.  
        GetUserStoreForDomain();  
  
    string filename = "options.txt";  
    try  
    {  
        // Checks to see if the options.txt file exists.  
        if (isoStore.GetFileNames(filename).GetLength(0) != 0)   
        {  
            // Opens the file because it exists.  
            System.IO.IsolatedStorage.IsolatedStorageFileStream isos =   
                new System.IO.IsolatedStorage.IsolatedStorageFileStream  
                    (filename, System.IO.FileMode.Open,isoStore);  
            System.IO.StreamReader reader = null;  
            try   
            {  
                reader = new System.IO.StreamReader(isos);  
  
                // Reads the values stored.  
                TypeConverter converter ;  
                converter = TypeDescriptor.GetConverter(typeof(Color));  
  
                this.MainButton.BackColor =   
                 (Color)(converter.ConvertFromString(reader.ReadLine()));  
                this.MainButton.ForeColor =   
                 (Color)(converter.ConvertFromString(reader.ReadLine()));  
  
                converter = TypeDescriptor.GetConverter(typeof(Font));  
                this.MainButton.Font =   
                  (Font)(converter.ConvertFromString(reader.ReadLine()));  
            }  
            catch (Exception ex)  
            {   
                System.Diagnostics.Debug.WriteLine  
                     ("Cannot read options " + ex.ToString());  
            }  
            finally  
            {  
                reader.Close();  
            }  
        }  
    }   
    catch (Exception ex)   
    {  
        System.Diagnostics.Debug.WriteLine  
            ("Cannot read options " + ex.ToString());  
    }  
}  
  
// Writes the button options to the isolated storage.  
public void Write()   
{  
    System.IO.IsolatedStorage.IsolatedStorageFile isoStore =   
        System.IO.IsolatedStorage.IsolatedStorageFile.  
        GetUserStoreForDomain();  
  
    string filename = "options.txt";  
    try   
    {  
        // Checks if the file exists and, if it does, tries to delete it.  
        if (isoStore.GetFileNames(filename).GetLength(0) != 0)   
        {  
            isoStore.DeleteFile(filename);  
        }  
    }  
    catch (Exception ex)   
    {  
        System.Diagnostics.Debug.WriteLine  
            ("Cannot delete file " + ex.ToString());  
    }  
  
    // Creates the options file and writes the button options to it.  
    System.IO.StreamWriter writer = null;  
    try   
    {  
        System.IO.IsolatedStorage.IsolatedStorageFileStream isos = new   
            System.IO.IsolatedStorage.IsolatedStorageFileStream(filename,   
            System.IO.FileMode.CreateNew,isoStore);  
  
        writer = new System.IO.StreamWriter(isos);  
        TypeConverter converter ;  
  
        converter = TypeDescriptor.GetConverter(typeof(Color));  
        writer.WriteLine(converter.ConvertToString(  
            this.MainButton.BackColor));  
        writer.WriteLine(converter.ConvertToString(  
            this.MainButton.ForeColor));  
  
        converter = TypeDescriptor.GetConverter(typeof(Font));  
        writer.WriteLine(converter.ConvertToString(  
            this.MainButton.Font));  
  
    }  
    catch (Exception ex)  
    {   
        System.Diagnostics.Debug.WriteLine  
           ("Cannot write options " + ex.ToString());  
    }  
    finally  
    {  
        writer.Close();  
    }  
}  
```  
  
## <a name="database-access"></a><span data-ttu-id="ce0e5-151">Accès à la base de données</span><span class="sxs-lookup"><span data-stu-id="ce0e5-151">Database Access</span></span>  
 <span data-ttu-id="ce0e5-152">Les autorisations nécessaires pour accéder à une base de données varient en fonction du fournisseur de base de données. Toutefois, seules les applications qui s'exécutent avec les autorisations appropriées peuvent accéder à une base de données via une connexion de données.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-152">The permissions required to access a database vary based on the database provider; however, only applications that are running with the appropriate permissions can access a database through a data connection.</span></span> <span data-ttu-id="ce0e5-153">Pour plus d’informations sur les autorisations requises pour accéder à une base de données, consultez [sécurité d’accès du code et ADO.net](../data/adonet/code-access-security.md).</span><span class="sxs-lookup"><span data-stu-id="ce0e5-153">For more information about the permissions that are required to access a database, see [Code Access Security and ADO.NET](../data/adonet/code-access-security.md).</span></span>  
  
 <span data-ttu-id="ce0e5-154">Si vous ne pouvez pas accéder directement à une base de données car vous souhaitez que votre application s'exécute en mode de confiance partielle, vous pouvez utiliser un service web comme alternative pour accéder à vos données.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-154">If you cannot directly access a database because you want your application to run in partial trust, you can use a Web service as an alternative means to access your data.</span></span> <span data-ttu-id="ce0e5-155">Un service web est un élément logiciel accessible par programmation sur un réseau.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-155">A Web service is a piece of software that can be programmatically accessed over a network.</span></span> <span data-ttu-id="ce0e5-156">Avec les services web, les applications peuvent partager des données entre des zones de groupe de code.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-156">With Web services, applications can share data across code group zones.</span></span> <span data-ttu-id="ce0e5-157">Par défaut, les applications des zones Intranet local et Internet sont autorisées à accéder à leurs sites d'origine, ce qui leur permet d'appeler un service web hébergé sur le même serveur.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-157">By default, applications in the local intranet and Internet zones are granted the right to access their sites of origin, which enables them to call a Web service hosted on the same server.</span></span> <span data-ttu-id="ce0e5-158">Pour plus d’informations [, consultez services Web dans ASP.NET AJAX](https://docs.microsoft.com/previous-versions/aspnet/bb398785(v=vs.100)) ou [Windows Communication Foundation](../wcf/index.md).</span><span class="sxs-lookup"><span data-stu-id="ce0e5-158">For more information see [Web Services in ASP.NET AJAX](https://docs.microsoft.com/previous-versions/aspnet/bb398785(v=vs.100)) or [Windows Communication Foundation](../wcf/index.md).</span></span>  
  
## <a name="registry-access"></a><span data-ttu-id="ce0e5-159">Accès au Registre</span><span class="sxs-lookup"><span data-stu-id="ce0e5-159">Registry Access</span></span>  
 <span data-ttu-id="ce0e5-160">La classe <xref:System.Security.Permissions.RegistryPermission> contrôle l'accès au Registre du système d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-160">The <xref:System.Security.Permissions.RegistryPermission> class controls access to the operating system registry.</span></span> <span data-ttu-id="ce0e5-161">Par défaut, seules les applications qui s'exécutent localement peuvent accéder au Registre.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-161">By default, only applications that are running locally can access the registry.</span></span>  <span data-ttu-id="ce0e5-162"><xref:System.Security.Permissions.RegistryPermission> accorde uniquement à une application le droit de tenter d'accéder au Registre. Il ne garantit pas la réussite de l'accès, car le système d'exploitation applique quand même la sécurité sur le Registre.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-162"><xref:System.Security.Permissions.RegistryPermission> only grants an application the right to try registry access; it does not guarantee access will succeed, because the operating system still enforces security on the registry.</span></span>  
  
 <span data-ttu-id="ce0e5-163">Étant donné que vous ne pouvez pas accéder au Registre avec une confiance partielle, vous devrez peut-être trouver d'autres méthodes pour stocker vos données.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-163">Because you cannot access the registry under partial trust, you may need to find other methods of storing your data.</span></span> <span data-ttu-id="ce0e5-164">Quand vous stockez des paramètres d'application, utilisez le stockage isolé plutôt que le Registre.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-164">When you store application settings, use isolated storage instead of the registry.</span></span> <span data-ttu-id="ce0e5-165">Vous pouvez aussi utiliser le stockage isolé pour stocker d'autres fichiers spécifiques à l'application.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-165">Isolated storage can also be used to store other application-specific files.</span></span> <span data-ttu-id="ce0e5-166">Vous pouvez stocker des informations d'application globales relatives au serveur ou au site d'origine, car par défaut une application a le droit d'accéder au site de son origine.</span><span class="sxs-lookup"><span data-stu-id="ce0e5-166">You can also store global application information about the server or site of origin, because by default an application is granted the right to access the site of its origin.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce0e5-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ce0e5-167">See also</span></span>

- [<span data-ttu-id="ce0e5-168">Impression plus sécurisée dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ce0e5-168">More Secure Printing in Windows Forms</span></span>](more-secure-printing-in-windows-forms.md)
- [<span data-ttu-id="ce0e5-169">Considérations supplémentaires sur la sécurité des Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ce0e5-169">Additional Security Considerations in Windows Forms</span></span>](additional-security-considerations-in-windows-forms.md)
- [<span data-ttu-id="ce0e5-170">Vue d’ensemble de la sécurité dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ce0e5-170">Security in Windows Forms Overview</span></span>](security-in-windows-forms-overview.md)
- [<span data-ttu-id="ce0e5-171">Sécurité de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ce0e5-171">Windows Forms Security</span></span>](windows-forms-security.md)
- [<span data-ttu-id="ce0e5-172">Mage.exe (outil Manifest Generation and Editing)</span><span class="sxs-lookup"><span data-stu-id="ce0e5-172">Mage.exe (Manifest Generation and Editing Tool)</span></span>](../tools/mage-exe-manifest-generation-and-editing-tool.md)
- [<span data-ttu-id="ce0e5-173">MageUI.exe (outil Manifest Generation and Editing, client graphique)</span><span class="sxs-lookup"><span data-stu-id="ce0e5-173">MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)</span></span>](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
