---
title: Portées de nom XAML WPF
ms.date: 03/30/2017
helpviewer_keywords:
- namescopes [WPF]
- styles [WPF], namescopes in
- templates [WPF], namescopes in
- APIs [WPF], name-related
- name-related APIs
- XAML [WPF], namescopes
- classes [WPF], FrameworkContentElement
ms.assetid: 52bbf4f2-15fc-40d4-837b-bb4c21ead7d4
ms.openlocfilehash: edf5c8a828bea182cd87542276fb7eb2df1908be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917336"
---
# <a name="wpf-xaml-namescopes"></a>Portées de nom XAML WPF
Les portées de nom XAML correspondent à un concept qui identifie des objets définis en XAML. Les noms dans une portée de nom XAML peuvent être utilisés pour établir des relations entre les noms définis en XAML des objets et leurs instances équivalentes dans une arborescence d’objets. En règle générale, les portées de nom XAML dans du code managé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont créées lors du chargement des racines d’une page XAML spécifique pour une application XAML. Les portées de code XAML, comme l’objet <xref:System.Windows.Markup.INameScope> de programmation, sont définies par l’interface et <xref:System.Windows.NameScope>sont également implémentées par la classe pratique.  

<a name="Namescopes_in_Loaded_XAML_Applications"></a>   
## <a name="namescopes-in-loaded-xaml-applications"></a>Portées de nom dans les applications XAML chargées  
 Dans un contexte plus large de programmation ou d’informatique, les concepts de programmation incluent souvent le principe d’un identificateur ou d’un nom unique, qui peut être utilisé pour accéder à un objet. Pour les systèmes qui utilisent des identificateurs ou des noms, la portée de nom définit les limites à l’intérieur desquelles un processus ou une technique recherche si un objet de ce nom est demandé, ou les limites dans lesquelles l’unicité des noms qui identifient est appliquée. Ces principes généraux sont vrais pour les portées de nom XAML. Dans WPF, les portées de nom XAML sont créées sur l’élément racine d’une page XAML quand la page est chargée. Chaque nom spécifié dans la page XAML en commençant à la racine de la page est ajouté à une portée de nom XAML pertinente.  
  
 Dans le XAML WPF, les éléments qui sont des éléments racines courants <xref:System.Windows.Controls.Page>(tels <xref:System.Windows.Window>que et) contrôlent toujours une portée de code XAML. Si un élément tel que <xref:System.Windows.FrameworkElement> ou <xref:System.Windows.FrameworkContentElement> est l’élément racine de la page dans le balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , un processeur <xref:System.Windows.Controls.Page> ajoute une racine implicitement afin <xref:System.Windows.Controls.Page> que le puisse fournir une portée de code XAML opérationnelle.  
  
> [!NOTE]
> Les actions de génération WPF créent une portée de nom XAML pour une production XAML même si aucun attribut `Name` ou `x:Name` n’est défini sur les éléments dans la balisage [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 Si vous essayez d’utiliser deux fois le même nom dans une portée de nom XAML, une exception est levée. Pour du XAML WPF qui a du code-behind et qui fait partie d’une application compilée, l’exception est levée au moment de la génération par les actions de génération WPF, lors de la création de la classe générée pour la page pendant la compilation initiale du balisage. Pour le XAML qui n’est compilé par balisage par aucune action de génération, des exceptions liées aux problèmes de portée de nom XAML peuvent être déclenchées lors du chargement du XAML. Les concepteurs XAML peuvent également anticiper les problèmes de portée de nom XAML au moment du design.  
  
### <a name="adding-objects-to-runtime-object-trees"></a>Ajout d’objets à des arborescences d’objets d’exécution  
 Le moment où le XAML est analysé correspond au moment une portée de nom XAML WPF est créée et définie. Si vous ajoutez un objet à une arborescence d’objets après l’analyse du code XAML ayant généré cette arborescence, une valeur `Name` ou `x:Name` sur le nouvel objet ne met pas automatiquement à jour les informations contenues dans une portée de nom XAML. Pour ajouter un nom pour un objet dans une portée de nom XAML WPF après le chargement du code XAML, vous devez appeler <xref:System.Windows.Markup.INameScope.RegisterName%2A> l’implémentation appropriée de sur l’objet qui définit la portée de nom XAML, qui est généralement la racine de la page XAML. Si le nom n’est pas inscrit, l’objet ajouté ne peut pas être référencé par nom via des <xref:System.Windows.FrameworkElement.FindName%2A>méthodes telles que, et vous ne pouvez pas utiliser ce nom pour le ciblage d’animation.  
  
 Le scénario le plus courant pour les développeurs d’applications est que <xref:System.Windows.FrameworkElement.RegisterName%2A> vous allez utiliser pour enregistrer des noms dans la portée de nom XAML sur la racine actuelle de la page. <xref:System.Windows.FrameworkElement.RegisterName%2A>fait partie d’un scénario important pour les storyboards qui ciblent des objets pour les animations. Pour plus d’informations, consultez [Vue d’ensemble des plans conceptuels](../graphics-multimedia/storyboards-overview.md).  
  
 Si vous appelez <xref:System.Windows.FrameworkElement.RegisterName%2A> sur un objet autre que l’objet qui définit la portée de nom XAML, le nom est toujours inscrit dans la portée de nom XAML dans laquelle l’objet appelant est conservé, comme <xref:System.Windows.FrameworkElement.RegisterName%2A> si vous aviez appelé sur la portée de nom XAML définissant l’objet.  
  
### <a name="xaml-namescopes-in-code"></a>Portées de nom XAML dans du code  
 Vous pouvez créer et ensuite utiliser des portées de nom XAML dans du code. Les API et les concepts impliqués dans la création de portée de nom XAML sont les mêmes, même pour une utilisation du code pure, car le processeur XAML pour [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise ces API et concepts quand il traite le XAML lui-même. Les concepts et l’API existent principalement pour pouvoir rechercher des objets par nom dans une arborescence d’objets définie partiellement ou entièrement en XAML.  
  
 Pour les applications créées par programme et non à partir du XAML chargé, l’objet qui définit une portée de code XAML doit <xref:System.Windows.Markup.INameScope>implémenter, ou <xref:System.Windows.FrameworkElement> être <xref:System.Windows.FrameworkContentElement> une classe ou dérivée, afin de prendre en charge la création d’une portée de code XAML sur son fois.  
  
 De même, pour tout élément qui n’est pas chargé et traité par un processeur XAML, la portée de nom XAML pour l’objet n’est pas créée ou initialisée par défaut. Vous devez créer explicitement une nouvelle portée de nom XAML pour tout objet dans lequel vous prévoyez d’inscrire des noms par la suite. Pour créer une portée de code XAML, vous appelez <xref:System.Windows.NameScope.SetNameScope%2A> la méthode statique. Spécifiez l’objet qui le possédera comme `dependencyObject` paramètre et un nouvel <xref:System.Windows.NameScope.%23ctor%2A> appel de constructeur comme `value` paramètre.  
  
 Si l’objet fourni comme `dependencyObject` pour <xref:System.Windows.NameScope.SetNameScope%2A> n’est pas <xref:System.Windows.Markup.INameScope> une implémentation <xref:System.Windows.FrameworkElement> , <xref:System.Windows.FrameworkContentElement>ou si <xref:System.Windows.FrameworkElement.RegisterName%2A> l’appel de sur n’importe quel élément enfant n’aura aucun effet. Si vous ne parvenez pas à créer la nouvelle portée de code XAML <xref:System.Windows.FrameworkElement.RegisterName%2A> explicitement, les appels à lèveront une exception.  
  
 Pour obtenir un exemple d’utilisation des API de portée de nom XAML dans du code, consultez [Définir une portée de nom](../graphics-multimedia/how-to-define-a-name-scope.md).  
  
<a name="Namescopes_in_Styles_and_Templates"></a>   
## <a name="xaml-namescopes-in-styles-and-templates"></a>Portées de nom XAML dans les styles et les modèles  
 Les styles et les modèles dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] permettent de réutiliser et de réappliquer le contenu d’une manière simple. Toutefois, les styles et les modèles peuvent également inclure des éléments avec des noms XAML définis au niveau d’un modèle. Ce même modèle peut être utilisé plusieurs fois dans une page. Pour cette raison, les styles et les modèles définissent tous deux leurs propres portées de nom XAML, indépendamment de l’emplacement où le style ou le modèle est appliqué dans une arborescence d’objets.  
  
 Prenons l'exemple suivant :  
  
 [!code-xaml[XamlOvwSupport#NameScopeTemplates](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 Ici, le même modèle est appliqué à deux boutons différents. Si les modèles n’avaient pas de portées de nom XAML discrètes, le nom `TheBorder` utilisé dans le modèle provoquerait un conflit de noms dans la portée de nom XAML. Chaque instanciation du modèle a sa propre portée de nom XAML. Ainsi, dans cet exemple, la portée de nom XAML de chaque modèle instancié contient un et un seul nom.  
  
 Les styles définissent également leur propre portée de nom XAML, principalement pour que des noms particuliers puissent être affectés aux différentes parties des plans conceptuels. Ces noms activent des comportements spécifiques des contrôles qui ciblent les éléments de ce nom, même si le modèle a été redéfini dans le cadre de la personnalisation du contrôle.  
  
 En raison des portées de nom XAML distinctes, rechercher des éléments nommés dans un modèle est plus difficile que rechercher dans une page un élément nommé non basé sur un modèle. Vous devez d’abord déterminer le modèle appliqué, en obtenant <xref:System.Windows.Controls.Control.Template%2A> la valeur de propriété du contrôle où le modèle est appliqué. Ensuite, vous appelez la version de modèle <xref:System.Windows.FrameworkTemplate.FindName%2A>de, en passant le contrôle où le modèle a été appliqué comme deuxième paramètre.  
  
 Si vous êtes un auteur de contrôle et que vous générez une Convention où un élément nommé particulier dans un modèle appliqué est la cible d’un comportement défini par le contrôle lui-même, vous pouvez <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> utiliser la méthode à partir du code d’implémentation de votre contrôle. La <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> méthode est protégée, donc seul l’auteur du contrôle y a accès.  
  
 Si vous travaillez à partir d’un modèle et que vous devez accéder à la portée de code XAML où le modèle est appliqué, récupérez <xref:System.Windows.FrameworkElement.TemplatedParent%2A>la valeur de, <xref:System.Windows.FrameworkElement.FindName%2A> puis appelez ici. Un exemple de travail à l’intérieur du modèle est l’écriture de l’implémentation du gestionnaire d’événements là où l’événement est déclenché à partir d’un élément dans un modèle appliqué.  
  
<a name="Namescopes_and_Name_related_APIs"></a>   
## <a name="xaml-namescopes-and-name-related-apis"></a>Portées de nom XAML et API relatives aux noms  
 <xref:System.Windows.FrameworkElement>a <xref:System.Windows.FrameworkElement.FindName%2A>les méthodes et<xref:System.Windows.FrameworkElement.UnregisterName%2A> . <xref:System.Windows.FrameworkElement.RegisterName%2A> Si l’objet sur lequel vous appelez ces méthodes a une portée de nom XAML, les méthodes font les appels au sein des méthodes de la portée de nom XAML appropriée. Sinon, l’élément parent est vérifié pour voir s’il détient une portée de nom XAML, et ce processus continue de manière récursive jusqu’à ce qu’une portée de nom XAML soit trouvée (en raison du comportement du processeur XAML, la présence d’une portée de nom XAML à la racine est garantie). <xref:System.Windows.FrameworkContentElement>a des comportements analogues, à l’exception du <xref:System.Windows.FrameworkContentElement> fait qu’aucune n’aura jamais une portée de code XAML. Les méthodes existent sur <xref:System.Windows.FrameworkContentElement> afin que les appels puissent être transférés finalement à un <xref:System.Windows.FrameworkElement> élément parent.  
  
 <xref:System.Windows.NameScope.SetNameScope%2A>est utilisé pour mapper une nouvelle portée de code XAML à un objet existant. Vous pouvez appeler <xref:System.Windows.NameScope.SetNameScope%2A> plusieurs fois pour réinitialiser ou effacer la portée de code XAML, mais cela n’est pas une utilisation courante. En outre <xref:System.Windows.NameScope.GetNameScope%2A> , n’est généralement pas utilisé à partir du code.  
  
### <a name="xaml-namescope-implementations"></a>Implémentations de portée de nom XAML  
 Les classes suivantes implémentent <xref:System.Windows.Markup.INameScope> directement:  
  
- <xref:System.Windows.NameScope>  
  
- <xref:System.Windows.Style>  
  
- <xref:System.Windows.ResourceDictionary>  
  
- <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary>n’utilise pas de noms ou de portées de nom XAML; elle utilise à la place des clés, car il s’agit d’une implémentation de dictionnaire. La seule raison pour <xref:System.Windows.ResourceDictionary> laquelle <xref:System.Windows.Markup.INameScope> implémente est de pouvoir lever des exceptions au code utilisateur qui permettent de clarifier la distinction entre une véritable portée de code <xref:System.Windows.ResourceDictionary> XAML et la manière dont un gère les clés, ainsi que de s’assurer que les portées de code XAML ne sont pas appliquées à un <xref:System.Windows.ResourceDictionary> par les éléments parents.  
  
 <xref:System.Windows.FrameworkTemplate>et <xref:System.Windows.Style> implémentent <xref:System.Windows.Markup.INameScope> via des définitions d’interface explicites. Les implémentations explicites permettent à ces portées de code XAML de se comporter de façon <xref:System.Windows.Markup.INameScope> conventionnelle quand elles sont accessibles via l’interface, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ce qui explique comment les portées de code XAML sont communiquées par les processus internes. Toutefois, les définitions d’interface explicites ne font pas partie de la <xref:System.Windows.FrameworkTemplate> surface <xref:System.Windows.Style>d’API conventionnelle de et, parce que vous <xref:System.Windows.FrameworkTemplate> devez <xref:System.Windows.Style> rarement appeler les méthodes sur et directement, et utiliser à la <xref:System.Windows.Markup.INameScope> place une autre API tels que <xref:System.Windows.FrameworkElement.GetTemplateChild%2A>.  
  
 Les classes suivantes définissent leur propre portée de code XAML <xref:System.Windows.NameScope?displayProperty=nameWithType> , en utilisant la classe d’assistance et en se connectant <xref:System.Windows.NameScope.NameScope%2A?displayProperty=nameWithType> à son implémentation de portée de code XAML par le biais de la propriété jointe:  
  
- <xref:System.Windows.FrameworkElement>  
  
- <xref:System.Windows.FrameworkContentElement>  
  
## <a name="see-also"></a>Voir aussi

- [Espaces de noms XAML et mappage d'espace de noms pour XAML WPF](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)
- [x:Name, directive](../../xaml-services/x-name-directive.md)
