# Rsync

## Quick ref

Mirror src/ dir to dest dir dst/.

    rsync -avhpn src/ dst/
    # Remove n option to turn off dry run.
    # With trailing slash on src/, src is not created in dst.
    # With out slash "src", then get dst/src/...
