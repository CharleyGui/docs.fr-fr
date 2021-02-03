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
# <a name="native-code-cant-access-windows-forms-objects"></a><span data-ttu-id="04324-103">Le code natif ne peut pas accéder aux objets Windows Forms</span><span class="sxs-lookup"><span data-stu-id="04324-103">Native code can't access Windows Forms objects</span></span>

<span data-ttu-id="04324-104">À compter de .NET 5,0, vous ne pouvez plus accéder aux objets Windows Forms à partir du code natif.</span><span class="sxs-lookup"><span data-stu-id="04324-104">Starting in .NET 5.0, you can no longer access Windows Forms objects from native code.</span></span>

## <a name="change-description"></a><span data-ttu-id="04324-105">Description de la modification</span><span class="sxs-lookup"><span data-stu-id="04324-105">Change description</span></span>

<span data-ttu-id="04324-106">Dans les versions précédentes de .NET, certains types de Windows Forms étaient décorés comme visibles pour COM Interop et étaient donc accessibles au code natif.</span><span class="sxs-lookup"><span data-stu-id="04324-106">In previous .NET versions, some Windows Forms types were decorated as visible to COM interop, and thus were accessible to native code.</span></span> <span data-ttu-id="04324-107">À compter de .NET 5,0, aucune API Windows Forms n’est visible pour COM Interop ou accessible en code natif.</span><span class="sxs-lookup"><span data-stu-id="04324-107">Starting in .NET 5.0, no Windows Forms API are visible to COM interop or accessible to native code.</span></span> <span data-ttu-id="04324-108">Le Runtime .NET ne prend plus en charge la création de bibliothèques de types personnalisées prêtes à l’emploi.</span><span class="sxs-lookup"><span data-stu-id="04324-108">The .NET runtime no longer supports creating custom type libraries out of the box.</span></span> <span data-ttu-id="04324-109">En outre, le Runtime .NET ne peut pas dépendre de la bibliothèque de types pour .NET Framework (ce qui nécessiterait la mise à jour de la forme des classes comme dans .NET Framework).</span><span class="sxs-lookup"><span data-stu-id="04324-109">In addition, the .NET runtime can't depend on the type library for .NET Framework (which would require maintaining the shape of classes as they were in .NET Framework).</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="04324-110">Motif de modification</span><span class="sxs-lookup"><span data-stu-id="04324-110">Reason for change</span></span>

- <span data-ttu-id="04324-111">Suppression de des `ComVisible(true)` énumérations utilisées pour la génération et la recherche de la bibliothèque de types (fichier TLB) : étant donné qu’il n’existe pas de fichier. tlb de WinForms fourni par .net Core, il n’y a aucune valeur pour conserver cet attribut.</span><span class="sxs-lookup"><span data-stu-id="04324-111">Removal of `ComVisible(true)` from enumerations that were used for type library (TLB file) generation and lookup: Since there is no WinForms TLB provided by .NET Core, there's no value in keeping this attribute.</span></span>
- <span data-ttu-id="04324-112">Suppression de `ComVisible(true)` à partir de `AccessibleObject` classes : les classes ne sont pas cocreatables (elles n’ont pas de constructeur sans paramètre) et l’exposition d’une instance déjà existante à com ne requiert pas cet attribut.</span><span class="sxs-lookup"><span data-stu-id="04324-112">Removal of `ComVisible(true)` from `AccessibleObject` classes: The classes are not CoCreateable (they have no parameterless constructor), and exposing an already existing instance to COM does not require that attribute.</span></span>
- <span data-ttu-id="04324-113">Suppression des `ComVisible(true)` `Control` classes from et `Component` : utilisées pour permettre l’hébergement de contrôles WinForms via OLE/ActiveX, par exemple dans VB6 ou MFC.</span><span class="sxs-lookup"><span data-stu-id="04324-113">Removal of `ComVisible(true)` from `Control` and `Component` classes: This was used to allow hosting of WinForms controls via OLE/ActiveX, for example in VB6 or MFC.</span></span> <span data-ttu-id="04324-114">Toutefois, cela nécessite un TLB pour WinForms, qui n’est plus fourni, ainsi que l’activation basée sur le registre, qui ne fonctionne pas non plus.</span><span class="sxs-lookup"><span data-stu-id="04324-114">However, this requires a TLB for WinForms, which is no longer provided, as well as registry-based activation, which also would not work out of the box.</span></span> <span data-ttu-id="04324-115">En règle générale, il n’existait pas de maintenance de l’hébergement COM des contrôles WinForms. par conséquent, la prise en charge a été supprimée au lieu de la laisser dans un État non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="04324-115">Generally, there was no maintenance of COM-based hosting of WinForms controls, so support was removed instead of leaving it in an unsupported state.</span></span>
- <span data-ttu-id="04324-116">Suppression des `ClassInterface` attributs des contrôles : si l’hébergement via OLE/ActiveX n’est pas pris en charge, ces attributs ne sont plus nécessaires.</span><span class="sxs-lookup"><span data-stu-id="04324-116">Removal of `ClassInterface` attributes from controls: If hosting via OLE/ActiveX is not supported, these attributes aren't needed anymore.</span></span> <span data-ttu-id="04324-117">Ils sont conservés dans d’autres endroits où les objets sont toujours exposés à COM et l’attribut peut être pertinent.</span><span class="sxs-lookup"><span data-stu-id="04324-117">They are kept in other places where objects are still exposed to COM and the attribute may be relevant.</span></span>
- <span data-ttu-id="04324-118">Suppression de `ComVisible(true)` à partir de `EventArgs` : ils étaient très probablement utilisés avec l’hébergement OLE/ActiveX, qui n’est plus pris en charge.</span><span class="sxs-lookup"><span data-stu-id="04324-118">Removal of `ComVisible(true)` from `EventArgs`: They were most likely used with OLE/ActiveX hosting, which is no longer supported.</span></span> <span data-ttu-id="04324-119">Ils ne sont pas cocreatables non plus. l’attribut n’a donc aucun effet.</span><span class="sxs-lookup"><span data-stu-id="04324-119">They are not CoCreateable either, so the attribute has no purpose.</span></span> <span data-ttu-id="04324-120">En outre, l’exposition d’instances existantes sans fournir un TLB n’est pas justifiée.</span><span class="sxs-lookup"><span data-stu-id="04324-120">Also, exposing existing instances without providing a TLB makes no sense.</span></span>
- <span data-ttu-id="04324-121">Suppression de des `ComVisible(true)` délégués : l’objectif est inconnu, mais étant donné que l’hébergement ActiveX des contrôles WinForms n’est plus pris en charge, il est peu probable qu’il soit utile.</span><span class="sxs-lookup"><span data-stu-id="04324-121">Removal of `ComVisible(true)` from delegates: Purpose is unknown, but since ActiveX hosting of WinForms Controls is no longer supported, it's unlikely to have any usefulness.</span></span>
- <span data-ttu-id="04324-122">Suppression de `ComVisible(true)` à partir de code non public : le seul consommateur potentiel est le nouveau concepteur Visual Studio, mais sans un GUID spécifié, il est peu probable qu’il soit toujours nécessaire.</span><span class="sxs-lookup"><span data-stu-id="04324-122">Removal of `ComVisible(true)` from some non-public code: The only potential consumer would be the new Visual Studio designer, but without a GUID specified, it's unlikely that it's still needed.</span></span>
- <span data-ttu-id="04324-123">Suppression de `ComVisible(true)` certaines classes de concepteur publics arbitraires : l’ancien concepteur Visual Studio a peut-être utilisé COM Interop pour communiquer avec ces classes.</span><span class="sxs-lookup"><span data-stu-id="04324-123">Removal of `ComVisible(true)` from some arbitrary public designer classes: The old Visual Studio designer may have been using COM interop to talk to these classes.</span></span> <span data-ttu-id="04324-124">Toutefois, l’ancien concepteur ne prend pas en charge .NET Core, donc peu de personnes en ont besoin `ComVisible` .</span><span class="sxs-lookup"><span data-stu-id="04324-124">However, the old designer doesn't support .NET Core, so few people would need these as `ComVisible`.</span></span>
- <span data-ttu-id="04324-125">`IWin32Window` définit le même GUID qui a été défini dans .NET Framework, ce qui a des conséquences dangereuses.</span><span class="sxs-lookup"><span data-stu-id="04324-125">`IWin32Window` defined the same GUID that was defined in .NET Framework, which has dangerous consequences.</span></span> <span data-ttu-id="04324-126">Si vous avez besoin d’une interopérabilité avec .NET Framework, utilisez `ComImport` .</span><span class="sxs-lookup"><span data-stu-id="04324-126">If you require interop with .NET Framework, use `ComImport`.</span></span>
- <span data-ttu-id="04324-127">Le WinForms géré `IDataObject` a été créé `ComVisible` .</span><span class="sxs-lookup"><span data-stu-id="04324-127">The WinForms managed `IDataObject` was made `ComVisible`.</span></span> <span data-ttu-id="04324-128">Ce n’est pas obligatoire, mais il existe une `ComImport` déclaration d’interface distincte pour `IDataObject` COM Interop.</span><span class="sxs-lookup"><span data-stu-id="04324-128">This is not required, there is a separate `ComImport` interface declaration for `IDataObject` COM interop.</span></span> <span data-ttu-id="04324-129">Il est contre-productif d' `IDataObject` être géré `ComVisible` , car aucun TLB n’est fourni et le marshaling échouera toujours.</span><span class="sxs-lookup"><span data-stu-id="04324-129">It's counterproductive to have the managed `IDataObject` be `ComVisible`, since no TLB is provided and marshaling will always fail.</span></span> <span data-ttu-id="04324-130">En outre, le GUID n’a pas été spécifié et est différent de .NET Framework, donc il est peu probable que la suppression d’un IID non documenté affecte les clients de manière négative.</span><span class="sxs-lookup"><span data-stu-id="04324-130">Also, the GUID was not specified and differed from .NET Framework, so its unlikely that removing an undocumented IID will affect customers negatively.</span></span>
- <span data-ttu-id="04324-131">Suppression de `ComVisible(false)` : celles-ci sont placées dans des emplacements apparemment arbitraires et sont redondantes lorsque la valeur par défaut est de ne pas exposer les classes à COM Interop.</span><span class="sxs-lookup"><span data-stu-id="04324-131">Removal of `ComVisible(false)`: Those are placed in seemingly arbitrary places and are redundant when the default is to not expose classes to COM interop.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="04324-132">Version introduite</span><span class="sxs-lookup"><span data-stu-id="04324-132">Version introduced</span></span>

<span data-ttu-id="04324-133">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="04324-133">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="04324-134">Action recommandée</span><span class="sxs-lookup"><span data-stu-id="04324-134">Recommended action</span></span>

<span data-ttu-id="04324-135">L’exemple suivant fonctionne sur .NET Framework et .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="04324-135">The following example works on .NET Framework and .NET Core 3.1.</span></span> <span data-ttu-id="04324-136">Cet exemple s’appuie sur la bibliothèque de types .NET Framework, qui permet au code JavaScript de rappeler la sous-classe de formulaire par le biais de la réflexion.</span><span class="sxs-lookup"><span data-stu-id="04324-136">This example relies on the .NET Framework type library, which allows the JavaScript to call back into the form subclass via reflection.</span></span>

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

<span data-ttu-id="04324-137">Il existe deux façons de faire fonctionner l’exemple sur .NET 5,0 et versions ultérieures :</span><span class="sxs-lookup"><span data-stu-id="04324-137">There are two possible ways to make the example work on .NET 5.0 and later versions:</span></span>

- <span data-ttu-id="04324-138">Introduisez un objet déclaré par `ObjectForScripting` l’utilisateur qui prend en charge `IDispatch` (qui est appliqué par défaut, sauf s’il a été modifié explicitement au niveau du projet).</span><span class="sxs-lookup"><span data-stu-id="04324-138">Introduce a user-declared `ObjectForScripting` object that supports `IDispatch` (which is applied by default, unless changed explicitly at the project level).</span></span>

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

- <span data-ttu-id="04324-139">Déclarez une interface avec les méthodes à exposer.</span><span class="sxs-lookup"><span data-stu-id="04324-139">Declare an interface with the methods to expose.</span></span>

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

## <a name="affected-apis"></a><span data-ttu-id="04324-140">API affectées</span><span class="sxs-lookup"><span data-stu-id="04324-140">Affected APIs</span></span>

<span data-ttu-id="04324-141">Toutes les API Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="04324-141">All Windows Forms APIs.</span></span>

<!--

### Category

- Windows Forms

-->
