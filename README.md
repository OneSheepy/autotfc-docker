# 1. Generate forge server files

Apply the included docker-compose file

```bash
docker-compose up -d
```

Once the server is up and running, stop it

```bash
docker stop autotfc
```

# 2. Apply the modpack files

Once docker is done generating needed files, we need to apply changes from modpack and mods.

In the modpack there is `overrides` folder. In there are 3 folders that need to be copied over.

Content from `defaultconfigs` needs to be copied over into server's `defaultconfigs` folder.

```bash
cp -r modpack/overrides/defaultconfigs/* server/defaultconfigs/
```

The `kubejs` and `patchouli_books` folders need to be placed into the root of server folder.

```bash
cp -r modpack/overrides/kubejs server/kubejs
cp -r modpack/overrides/patchouli_books server/patchouli_books
```

# 3. Download mods

If you use Prism Launcher then you can get all the mod .jar files just from your instance. Copy those over into the server's `mods` folder

```bash
cp -r <your_prism_instance>/mods/* server/mods/
```

If you don't have the mods like that, you need to download them from their respective pages. The AutoTFC modpack has a `modlist.html` file, that has links to all the mods used so you can get all the mods using that.

# 4. Generate TFC world

When server started, it generated regular vanilla world. To use the TFC world generation, go to the `server.properties` file in the server root folder and change the `level-type` value to `tfc:tng`.

Once that is changed, delete the `world` folder to force the server to regenerate everything.

```bash
rm -rf server/world
```

# 5. All done (hopefully)

Now start up docker container again

```bash
docker start autotfc
```

Give it a minute or two to regenerate world and then it should be done. Have fun :)
