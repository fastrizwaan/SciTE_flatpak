# SciTE_flatpak
Scintilla based SciTE Text Editor: Scite GTK flatpak 

#### install flathub repo and gnome sdk 3.38
```
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak install flathub org.gnome.Sdk/x86_64/3.38

```

#### clone and build flatpak from yaml
```
git clone https://github.com/fastrizwaan/SciTE_flatpak.git
cd SciTE_flatpak

# build
flatpak-builder --force-clean build-dir scite.yaml

# install 
flatpak-builder --user --install --force-clean build-dir scite.yaml

# run
flatpak run org.scintilla.SciTE
```

#### Build a flatpak bundle file from the above built repo:
```
flatpak-builder --repo="repo" --force-clean "build" scite.yaml
flatpak --user remote-add --no-gpg-verify "scite" "repo"
flatpak build-bundle "repo" "SciTE.flatpak" org.scintilla.SciTE  --runtime-repo="https://flathub.org/repo/flathub.flatpakrepo"

flatpak --user install SciTE.flatpak
flatpak run org.scintilla.SciTE
```
