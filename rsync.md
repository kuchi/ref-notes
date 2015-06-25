# Rsync

Important notes
- If you include the / in the source dir it won't make the dir. If you don't have
 the slash it will make the dir.

Copy certain files
    rsync -rvhn --include="*/" --include="**/*.png" --include="**/*.jpg" --exclude="**/*" Data /Volumes/ANTHONY-TD
