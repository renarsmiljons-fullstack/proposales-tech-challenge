# Components API

This page documents key exported components: props, behavior, and usage examples. Import paths shown are absolute.

## UI

### Button
- Import: `@/components/ui/button`
- Exports: `Button`, `buttonVariants`
- Props: extends `button` props; `variant` (`default|destructive|outline|secondary|ghost|link`), `size` (`default|sm|lg|icon`), `asChild`.
- Example:
```tsx
import { Button } from "@/components/ui/button";

export function Action() {
  return <Button variant="secondary" onClick={() => { /* ... */ }}>Save</Button>;
}
```

### Input
- Import: `@/components/ui/input`
- Exports: `Input`
- Example:
```tsx
import { Input } from "@/components/ui/input";

<Input placeholder="Email" type="email" />
```

### Checkbox
- Import: `@/components/ui/checkbox`
- Exports: `Checkbox`

### Alert
- Import: `@/components/ui/alert`
- Exports: `Alert`, `AlertTitle`, `AlertDescription`

### Dialog
- Import: `@/components/ui/dialog`
- Exports: `Dialog`, `DialogContent`, `DialogHeader`, `DialogTitle`, `DialogDescription`, `DialogFooter`, `DialogTrigger`, `DialogClose`

### Dropdown Menu
- Import: `@/components/ui/dropdown-menu`
- Exports: `DropdownMenu`, `DropdownMenuTrigger`, `DropdownMenuContent`, `DropdownMenuItem`, `DropdownMenuLabel`, `DropdownMenuSeparator`, `DropdownMenuGroup`, `DropdownMenuSub`, `DropdownMenuSubTrigger`, `DropdownMenuSubContent`, `DropdownMenuShortcut`

### Select
- Import: `@/components/ui/select`
- Exports: `Select`, `SelectTrigger`, `SelectValue`, `SelectContent`, `SelectGroup`, `SelectLabel`, `SelectItem`, `SelectSeparator`

### Tooltip
- Import: `@/components/ui/tooltip`
- Exports: `Tooltip`, `TooltipProvider`, `TooltipTrigger`, `TooltipContent`

### Sheet
- Import: `@/components/ui/sheet`
- Exports: `Sheet`, `SheetContent`, `SheetHeader`, `SheetTitle`, `SheetDescription`, `SheetFooter`, `SheetTrigger`, `SheetClose`

### Card
- Import: `@/components/ui/card`
- Exports: `Card`, `CardHeader`, `CardTitle`, `CardDescription`, `CardContent`, `CardFooter`

### Badge
- Import: `@/components/ui/badge`
- Exports: `Badge`, `badgeVariants`

### SiteLogo
- Import: `@/components/ui/site-logo`
- Props: `href?` string, `width?` number, `height?` number, `className?` string, `ariaLabel?` string
- Example:
```tsx
import { SiteLogo } from "@/components/ui/site-logo";

<SiteLogo href="/" />
```

### ThemeToggle
- Import: `@/components/ui/ThemeToggle`
- Description: Client component to toggle light/dark theme, persists to `localStorage`.
- Example:
```tsx
import { ThemeToggle } from "@/components/ui/ThemeToggle";

<ThemeToggle />
```

### FileUpload
- Import: `@/components/ui/file-upload`
- Props: `onUploadComplete(uuids: string[])`, `accept?` string, `multiple?` boolean, `disabled?` boolean, `maxFiles?` number
- Example:
```tsx
import { FileUpload } from "@/components/ui/file-upload";

<FileUpload onUploadComplete={(uuids) => console.log(uuids)} accept="image/*" />
```

### Sidebar System
- Import: `@/components/ui/sidebar`
- Exports: `SidebarProvider`, `Sidebar`, `SidebarTrigger`, `SidebarRail`, `SidebarInset`, `SidebarHeader`, `SidebarContent`, `SidebarFooter`, `SidebarSeparator`, `SidebarGroup`, `SidebarGroupLabel`, `SidebarGroupAction`, `SidebarGroupContent`, `SidebarMenu`, `SidebarMenuItem`, `SidebarMenuButton`, `SidebarMenuBadge`, `SidebarMenuAction`, `SidebarMenuSub`, `SidebarMenuSubItem`, `SidebarMenuSubButton`, `SidebarMenuSkeleton`, `useSidebar`
- Example:
```tsx
import { SidebarProvider, Sidebar, SidebarContent, SidebarHeader, SidebarInset } from "@/components/ui/sidebar";

<SidebarProvider>
  <Sidebar>
    <SidebarHeader>Header</SidebarHeader>
    <SidebarContent>Nav</SidebarContent>
  </Sidebar>
  <SidebarInset>Page</SidebarInset>
</SidebarProvider>
```

### Stepper
- Import: `@/components/ui/stepper`
- Exports: `defineStepper`
- Usage:
```tsx
import { defineStepper } from "@/components/ui/stepper";

const Steps = defineStepper(
  { id: "details", label: "Details" },
  { id: "confirm", label: "Confirm" }
);

export function Wizard() {
  const { Stepper, useStepper } = Steps;
  return (
    <Stepper.Provider>
      <Stepper.Navigation>
        <Stepper.Step of="details"><Stepper.Title>Details</Stepper.Title></Stepper.Step>
        <Stepper.Step of="confirm"><Stepper.Title>Confirm</Stepper.Title></Stepper.Step>
      </Stepper.Navigation>
      <Stepper.Panel>
        {/* content for current step */}
      </Stepper.Panel>
    </Stepper.Provider>
  );
}
```

## Additional UI Exports (quick reference)
- Avatar: `@/components/ui/avatar` → `Avatar`, `AvatarImage`, `AvatarFallback`
- Breadcrumb: `@/components/ui/breadcrumb` → `Breadcrumb`, `BreadcrumbList`, `BreadcrumbItem`, `BreadcrumbLink`, `BreadcrumbSeparator`, `BreadcrumbPage`
- Carousel: `@/components/ui/carousel` → `Carousel`, `CarouselContent`, `CarouselItem`, `CarouselPrevious`, `CarouselNext`, `type CarouselApi`
- Checkbox: `@/components/ui/checkbox` → `Checkbox`
- Collapsible: `@/components/ui/collapsible` → `Collapsible`, `CollapsibleTrigger`, `CollapsibleContent`
- Command: `@/components/ui/command` → `Command`, `CommandDialog`, `CommandEmpty`, `CommandGroup`, `CommandInput`, `CommandItem`, `CommandList`, `CommandSeparator`, `CommandShortcut`
- Input OTP: `@/components/ui/input-otp` → `InputOTP`, `InputOTPGroup`, `InputOTPSlot`, `InputOTPSeparator`
- Label: `@/components/ui/label` → `Label`
- Menubar: `@/components/ui/menubar` → `Menubar`, `MenubarMenu`, `MenubarTrigger`, `MenubarContent`, `MenubarGroup`, `MenubarItem`, `MenubarSeparator`, `MenubarSub`, `MenubarSubContent`, `MenubarSubTrigger`, `MenubarLabel`, `MenubarCheckboxItem`, `MenubarRadioGroup`, `MenubarRadioItem`, `MenubarShortcut`
- Popover: `@/components/ui/popover` → `Popover`, `PopoverTrigger`, `PopoverContent`, `PopoverAnchor`
- Separator: `@/components/ui/separator` → `Separator`
- Sheet: `@/components/ui/sheet` → see section above
- Skeleton: `@/components/ui/skeleton` → `Skeleton`
- Switch: `@/components/ui/switch` → `Switch`
- Textarea: `@/components/ui/textarea` → `Textarea`
- Toggle: `@/components/ui/toggle` → `Toggle`, `toggleVariants`
- Toggle Group: `@/components/ui/toggle-group` → `ToggleGroup`, `ToggleGroupItem`
- Tooltip: `@/components/ui/tooltip` → see section above
- Typography: `@/components/ui/Typography` → `TypographyH1`, `TypographyH2`, `TypographyH3`, `TypographyH4`, `TypographyP`, `TypographyLead`, `TypographyLarge`, `TypographySmall`, `TypographyMuted`

### Typography Example
```tsx
import { TypographyH1, TypographyP } from "@/components/ui/Typography";

<TypographyH1>Title</TypographyH1>
<TypographyP>Body text</TypographyP>
```

### BackButton
- Import: `@/components/ui/back-button`
- Description: Accessible back navigation button

### ButtonLoading
- Import: `@/components/ui/ButtonLoading`
- Description: A busy/loading button used inside forms

### ImageDisplayCard
- Import: `@/components/ui/image-display-card`
- Props: `url` string, `alt?` string, `className?` string, `onRemove?(): void`

## App Components

### Header
- Import: `@/components/headers`
- Props: `title?` string, `children?` ReactNode
- Example:
```tsx
import { Header } from "@/components/headers";

<Header title="Proposales" />
```

### AuthenticateDialog
- Import: `@/components/auth/authenticate-dialog`
- Props: `open` boolean, `onOpenChange(open:boolean)`, `onContinue(apiKey:string)`, `loading?` boolean

### CompanyCard
- Import: `@/components/company/company-card`
- Props: `company` Company, `isSelected?` boolean, `onSelectionChange?(selected:boolean)`

### CompanyDropdownMenuContent
- Import: `@/components/company/CompanyDropdownMenuContent`
- Props: `company` Company, `isMobile` boolean

## Providers

### AuthProvider
- Import: `@/components/providers/AuthProvider`
- Provides `AuthContext`; use via `useAuth()`
- Props: `children`, `initialAuth?`

### CreateProposalProvider
- Import: `@/components/providers/CreateProposalStateProvider`
- Provides `CreateProposalContext`; use via `useCreateProposalState()`
- Props: `children`, `initialProposal`

## Other App Components

### NavUser
- Import: `@/components/company/nav-user`
- Description: Displays authenticated company and dropdown actions

### Footer
- Import: `@/components/footer/Footer`
- Default export: `Footer`