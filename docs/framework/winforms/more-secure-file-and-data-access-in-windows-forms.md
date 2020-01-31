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
# <a name="more-secure-file-and-data-access-in-windows-forms"></a>Accès plus sécurisé aux fichiers et aux données dans les Windows Forms
Le .NET Framework utilise des autorisations pour protéger les ressources et les données. L'emplacement où votre application peut lire ou écrire des données dépend des autorisations qui lui sont accordées. Quand votre application s'exécute dans un environnement de confiance partielle, vous n'avez peut-être pas accès à vos données ou vous devrez peut-être modifier la manière dont vous accédez aux données.  
  
 Quand vous rencontrez une restriction de sécurité, vous avez deux options : déclarer l'autorisation (en supposant qu'elle a été accordée à votre application) ou utiliser une version de la fonctionnalité écrite pour fonctionner en mode de confiance partielle. Les sections suivantes décrivent comment gérer l'accès aux fichiers, aux bases de données et au Registre à partir d'applications qui s'exécutent dans un environnement de confiance partielle.  
  
> [!NOTE]
> Par défaut, les outils qui génèrent des déploiements ClickOnce ont par défaut ces déploiements qui demandent une confiance totale à partir des ordinateurs sur lesquels ils s’exécutent. Si vous souhaitez bénéficier des avantages de sécurité supplémentaires liés à l’exécution en mode de confiance partielle, vous devez modifier cette valeur par défaut dans Visual Studio ou dans l’un des outils de SDK Windows (Mage. exe ou MageUI. exe). Pour plus d’informations sur la sécurité Windows Forms et sur la façon de déterminer le niveau de confiance approprié pour votre application, consultez [vue d’ensemble de la sécurité dans Windows Forms](security-in-windows-forms-overview.md).  
  
## <a name="file-access"></a>Accès aux fichiers  
 La classe <xref:System.Security.Permissions.FileIOPermission> contrôle l’accès aux fichiers et aux dossiers dans le .NET Framework. Par défaut, le système de sécurité n'accorde pas <xref:System.Security.Permissions.FileIOPermission> aux environnements de confiance partielle tels que les zones Intranet local et Internet. Cependant, une application qui nécessite l'accès aux fichiers peut quand même fonctionner dans ces environnements si vous modifiez la conception de votre application ou si vous utilisez des méthodes différentes pour accéder aux fichiers. Par défaut, la zone Intranet local est autorisée à accéder au même site et au même répertoire, à se reconnecter au site de son origine et à lire à partir de son répertoire d'installation. Par défaut, la zone Internet est autorisée uniquement à se reconnecter au site de son origine.  
  
### <a name="user-specified-files"></a>Fichiers spécifiés par l'utilisateur  
 L'une des façons de gérer le fait de ne pas avoir l'autorisation d'accès aux fichiers consiste à inviter l'utilisateur à fournir des informations de fichiers spécifiques à l'aide de la classe <xref:System.Windows.Forms.OpenFileDialog> ou <xref:System.Windows.Forms.SaveFileDialog>. Cette interaction utilisateur permet de fournir une garantie que l'application ne peut pas remplacer des fichiers importants ou charger des fichiers privés à des fins malveillantes. Les méthodes <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> et <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> fournissent un accès en lecture et en écriture aux fichiers en ouvrant le flux de fichier pour le fichier spécifié par l'utilisateur. Ces méthodes aident aussi à protéger les fichiers de l’utilisateur en masquant leur chemin d’accès.  
  
> [!NOTE]
> Ces autorisations diffèrent selon que votre application est dans la zone Internet ou Intranet. Les applications de la zone Internet peuvent uniquement utiliser <xref:System.Windows.Forms.OpenFileDialog>, alors que les applications de la zone Intranet ont une autorisation Boîte de dialogue Fichier illimitée.  
  
 La classe <xref:System.Security.Permissions.FileDialogPermission> spécifie le type de boîte de dialogue Fichier que votre application peut utiliser. Le tableau suivant indique la valeur que vous devez avoir pour utiliser chaque classe <xref:System.Windows.Forms.FileDialog>.  
  
|Classe|Valeur d'accès nécessaire|  
|-----------|---------------------------|  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Open>|  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Save>|  
  
> [!NOTE]
> L'autorisation spécifique n'est pas demandée tant que la méthode <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> n'est pas appelée.  
  
 L'autorisation d'afficher une boîte de dialogue Fichier n'accorde pas à votre application un accès total à tous les membres des classes <xref:System.Windows.Forms.FileDialog>, <xref:System.Windows.Forms.OpenFileDialog> et <xref:System.Windows.Forms.SaveFileDialog>. Pour connaître les autorisations requises pour appeler chaque méthode, consultez la rubrique de référence pour cette méthode dans la documentation de la bibliothèque de classes .NET Framework.  
  
 L'exemple de code suivant utilise la méthode <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> pour ouvrir un fichier spécifié par l'utilisateur dans un contrôle <xref:System.Windows.Forms.RichTextBox>. L'exemple exige <xref:System.Security.Permissions.FileDialogPermission> et la valeur d'énumération <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> associée. Il illustre comment gérer <xref:System.Security.SecurityException> pour déterminer si la fonctionnalité d’enregistrement doit être désactivée. Cet exemple exige que votre <xref:System.Windows.Forms.Form> ait un contrôle <xref:System.Windows.Forms.Button> nommé `ButtonOpen` et un contrôle <xref:System.Windows.Forms.RichTextBox> nommé `RtfBoxMain`.  
  
> [!NOTE]
> La logique de programmation pour la fonctionnalité d’enregistrement n’est pas illustrée dans l’exemple.  
  
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
> Dans Visual C#, veillez à ajouter du code pour activer le gestionnaire d’événements. En utilisant le code de l'exemple précédent, le code suivant montre comment activer le gestionnaire d'événements.`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`  
  
### <a name="other-files"></a>Autres fichiers  
 Vous devrez parfois lire ou écrire dans des fichiers que l'utilisateur ne spécifie pas, par exemple quand vous devrez conserver les paramètres d'application. Dans les zones Intranet local et Internet, votre application ne sera pas autorisée à stocker des données dans un fichier local. Toutefois, elle pourra stocker des données dans un stockage isolé. Le stockage isolé est un compartiment de données abstrait (et non un emplacement de stockage spécifique) composé d'au moins un fichier de stockage isolé, appelé magasin, contenant les emplacements de répertoire réels où sont stockées les données. Les autorisations d'accès aux fichiers telles que <xref:System.Security.Permissions.FileIOPermission> ne sont pas nécessaires. Au lieu de cela, la classe <xref:System.Security.Permissions.IsolatedStoragePermission> contrôle les autorisations pour le stockage isolé. Par défaut, les applications qui s'exécutent dans les zones Intranet local et Internet peuvent stocker des données à l'aide du stockage isolé. Toutefois, des paramètres tels que les quotas de disque peuvent varier. Pour plus d’informations sur le stockage isolé, consultez [stockage isolé](../../standard/io/isolated-storage.md).  
  
 L'exemple suivant utilise le stockage isolé pour écrire des données dans un fichier situé dans un magasin. Cet exemple nécessite <xref:System.Security.Permissions.IsolatedStorageFilePermission> et la valeur d'énumération <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser>. Il illustre comment lire et écrire certaines valeurs de propriétés du contrôle <xref:System.Windows.Forms.Button> dans un fichier dans du stockage isolé. La fonction `Read` est appelée après le démarrage de l'application et la fonction `Write` est appelée avant la fin de l'application. L’exemple requiert que les fonctions `Read` et `Write` existent en tant que membres d’un <xref:System.Windows.Forms.Form> qui contient un contrôle <xref:System.Windows.Forms.Button> nommé `MainButton`.  
  
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
  
## <a name="database-access"></a>Accès à la base de données  
 Les autorisations nécessaires pour accéder à une base de données varient en fonction du fournisseur de base de données. Toutefois, seules les applications qui s'exécutent avec les autorisations appropriées peuvent accéder à une base de données via une connexion de données. Pour plus d’informations sur les autorisations requises pour accéder à une base de données, consultez [sécurité d’accès du code et ADO.net](../data/adonet/code-access-security.md).  
  
 Si vous ne pouvez pas accéder directement à une base de données car vous souhaitez que votre application s'exécute en mode de confiance partielle, vous pouvez utiliser un service web comme alternative pour accéder à vos données. Un service web est un élément logiciel accessible par programmation sur un réseau. Avec les services web, les applications peuvent partager des données entre des zones de groupe de code. Par défaut, les applications des zones Intranet local et Internet sont autorisées à accéder à leurs sites d'origine, ce qui leur permet d'appeler un service web hébergé sur le même serveur. Pour plus d’informations [, consultez services Web dans ASP.NET AJAX](https://docs.microsoft.com/previous-versions/aspnet/bb398785(v=vs.100)) ou [Windows Communication Foundation](../wcf/index.md).  
  
## <a name="registry-access"></a>Accès au Registre  
 La classe <xref:System.Security.Permissions.RegistryPermission> contrôle l'accès au Registre du système d'exploitation. Par défaut, seules les applications qui s'exécutent localement peuvent accéder au Registre.  <xref:System.Security.Permissions.RegistryPermission> accorde uniquement à une application le droit de tenter d'accéder au Registre. Il ne garantit pas la réussite de l'accès, car le système d'exploitation applique quand même la sécurité sur le Registre.  
  
 Étant donné que vous ne pouvez pas accéder au Registre avec une confiance partielle, vous devrez peut-être trouver d'autres méthodes pour stocker vos données. Quand vous stockez des paramètres d'application, utilisez le stockage isolé plutôt que le Registre. Vous pouvez aussi utiliser le stockage isolé pour stocker d'autres fichiers spécifiques à l'application. Vous pouvez stocker des informations d'application globales relatives au serveur ou au site d'origine, car par défaut une application a le droit d'accéder au site de son origine.  
  
## <a name="see-also"></a>Voir aussi

- [Impression plus sécurisée dans les Windows Forms](more-secure-printing-in-windows-forms.md)
- [Considérations supplémentaires sur la sécurité des Windows Forms](additional-security-considerations-in-windows-forms.md)
- [Vue d’ensemble de la sécurité dans les Windows Forms](security-in-windows-forms-overview.md)
- [Sécurité de Windows Forms](windows-forms-security.md)
- [Mage.exe (outil Manifest Generation and Editing)](../tools/mage-exe-manifest-generation-and-editing-tool.md)
- [MageUI.exe (outil Manifest Generation and Editing, client graphique)](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
