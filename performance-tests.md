# Performance Tests

## Test read write speed

Test writing

    gdd if=/dev/zero of=testfile0 bs=8k count=10000
    
Test reading

    gdd if=testfile0 of=/dev/null