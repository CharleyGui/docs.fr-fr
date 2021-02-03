---
title: 'Modification avec rupture : objets WinForms non accessibles à partir du code natif'
description: Découvrez la modification avec rupture dans .NET 5,0 où les objets Windows Forms ne sont plus accessibles à partir du code natif.
ms.date: 01/29/2021
ms.openlocfilehash: 53343f3f07817f735fa3b0ee77a352dcc80d4b6c
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99506571"
---
# <a name="native-code-cant-access-windows-forms-objects"></a>Le code natif ne peut pas accéder aux objets Windows Forms

À compter de .NET 5,0, vous ne pouvez plus accéder aux objets Windows Forms à partir du code natif.

## <a name="change-description"></a>Description de la modification

Dans les versions précédentes de .NET, certains types de Windows Forms étaient décorés comme visibles pour COM Interop et étaient donc accessibles au code natif. À compter de .NET 5,0, aucune API Windows Forms n’est visible pour COM Interop ou accessible en code natif. Le Runtime .NET ne prend plus en charge la création de bibliothèques de types personnalisées prêtes à l’emploi. En outre, le Runtime .NET ne peut pas dépendre de la bibliothèque de types pour .NET Framework (ce qui nécessiterait la mise à jour de la forme des classes comme dans .NET Framework).

## <a name="reason-for-change"></a>Motif de modification

- Suppression de des `ComVisible(true)` énumérations utilisées pour la génération et la recherche de la bibliothèque de types (fichier TLB) : étant donné qu’il n’existe pas de fichier. tlb de WinForms fourni par .net Core, il n’y a aucune valeur pour conserver cet attribut.
- Suppression de `ComVisible(true)` à partir de `AccessibleObject` classes : les classes ne sont pas cocreatables (elles n’ont pas de constructeur sans paramètre) et l’exposition d’une instance déjà existante à com ne requiert pas cet attribut.
- Suppression des `ComVisible(true)` `Control` classes from et `Component` : utilisées pour permettre l’hébergement de contrôles WinForms via OLE/ActiveX, par exemple dans VB6 ou MFC. Toutefois, cela nécessite un TLB pour WinForms, qui n’est plus fourni, ainsi que l’activation basée sur le registre, qui ne fonctionne pas non plus. En règle générale, il n’existait pas de maintenance de l’hébergement COM des contrôles WinForms. par conséquent, la prise en charge a été supprimée au lieu de la laisser dans un État non pris en charge.
- Suppression des `ClassInterface` attributs des contrôles : si l’hébergement via OLE/ActiveX n’est pas pris en charge, ces attributs ne sont plus nécessaires. Ils sont conservés dans d’autres endroits où les objets sont toujours exposés à COM et l’attribut peut être pertinent.
- Suppression de `ComVisible(true)` à partir de `EventArgs` : ils étaient très probablement utilisés avec l’hébergement OLE/ActiveX, qui n’est plus pris en charge. Ils ne sont pas cocreatables non plus. l’attribut n’a donc aucun effet. En outre, l’exposition d’instances existantes sans fournir un TLB n’est pas justifiée.
- Suppression de des `ComVisible(true)` délégués : l’objectif est inconnu, mais étant donné que l’hébergement ActiveX des contrôles WinForms n’est plus pris en charge, il est peu probable qu’il soit utile.
- Suppression de `ComVisible(true)` à partir de code non public : le seul consommateur potentiel est le nouveau concepteur Visual Studio, mais sans un GUID spécifié, il est peu probable qu’il soit toujours nécessaire.
- Suppression de `ComVisible(true)` certaines classes de concepteur publics arbitraires : l’ancien concepteur Visual Studio a peut-être utilisé COM Interop pour communiquer avec ces classes. Toutefois, l’ancien concepteur ne prend pas en charge .NET Core, donc peu de personnes en ont besoin `ComVisible` .
- `IWin32Window` définit le même GUID qui a été défini dans .NET Framework, ce qui a des conséquences dangereuses. Si vous avez besoin d’une interopérabilité avec .NET Framework, utilisez `ComImport` .
- Le WinForms géré `IDataObject` a été créé `ComVisible` . Ce n’est pas obligatoire, mais il existe une `ComImport` déclaration d’interface distincte pour `IDataObject` COM Interop. Il est contre-productif d' `IDataObject` être géré `ComVisible` , car aucun TLB n’est fourni et le marshaling échouera toujours. En outre, le GUID n’a pas été spécifié et est différent de .NET Framework, donc il est peu probable que la suppression d’un IID non documenté affecte les clients de manière négative.
- Suppression de `ComVisible(false)` : celles-ci sont placées dans des emplacements apparemment arbitraires et sont redondantes lorsque la valeur par défaut est de ne pas exposer les classes à COM Interop.

## <a name="version-introduced"></a>Version introduite

.NET 5.0

## <a name="recommended-action"></a>Action recommandée

L’exemple suivant fonctionne sur .NET Framework et .NET Core 3,1. Cet exemple s’appuie sur la bibliothèque de types .NET Framework, qui permet au code JavaScript de rappeler la sous-classe de formulaire par le biais de la réflexion.

```cs
[PermissionSet(SecurityAction.Demand, Name="FullTrust")]
[System.Runtime.InteropServices.ComVisibleAttribute(true)]
public class Form1 : Form
{
    private WebBrowser webBrowser1 = new WebBrowser();

    protected override void OnLoad(EventArgs e)
    {
        webBrowser1.AllowWebBrowserDrop = false;
        webBrowser1.IsWebBrowserContextMenuEnabled = false;
        webBrowser1.WebBrowserShortcutsEnabled = false;
        webBrowser1.ObjectForScripting = this;

        webBrowser1.DocumentText =
            "<html><body><button " +
            "onclick=\"window.external.Test('called from script code')\">" +
            "call client code from script code</button>" +
            "</body></html>";
    }

    public void Test(String message)
    {
        MessageBox.Show(message, "client code");
    }
}
```

Il existe deux façons de faire fonctionner l’exemple sur .NET 5,0 et versions ultérieures :

- Introduisez un objet déclaré par `ObjectForScripting` l’utilisateur qui prend en charge `IDispatch` (qui est appliqué par défaut, sauf s’il a été modifié explicitement au niveau du projet).

  ```cs
  public class MyScriptObject
  {
      private Form1 _form;

      public MyScriptObject(Form1 form)
      {
          _form = form;
      }

      public void Test(string message)
      {
          MessageBox.Show(message, "client code");
      }
  }

  public partial class Form1 : Form
  {
      protected override void OnLoad(EventArgs e)
      {
          ...

          // Works correctly.
          webBrowser1.ObjectForScripting = new MyScriptObject(this);

          ...
      }
  }
  ```

- Déclarez une interface avec les méthodes à exposer.

  ```cs
  public interface IForm1
  {
      void Test(string message);
  }

  [ComDefaultInterface(typeof(IForm1))]
  public partial class Form1 : Form, IForm1
  {
      protected override void OnLoad(EventArgs e)
      {
          ...

          // Works correctly.
          webBrowser1.ObjectForScripting = this;

          ...
      }
  }
  ```

## <a name="affected-apis"></a>API affectées

Toutes les API Windows Forms.

<!--

### Category

- Windows Forms

-->
