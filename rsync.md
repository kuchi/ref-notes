# Rsync

## Quick ref

Mirror src/ dir to dest dir dst/.

    rsync -avhpn src/ dst/
    # Remove n option to turn off dry run.
    # With trailing slash on src/, src is not created in dst.
    # With out slash "src", then get dst/src/...

Important notes
- If you include the / in the source dir it won't make the dir. If you don't have
 the slash it will make the dir.

Copy certain files
    
    rsync -rvhn --include="*/" --include="**/*.png" --include="**/*.jpg" --exclude="**/*" Data /Volumes/ANTHONY-TD
