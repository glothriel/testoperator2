# poc-mysql-operator
This operator shows possible error in Operator-SDK, regarding scoping.

### Demo

```
# Install molecule requirements
pip install -r requirements.txt

# Start test framework
molecule converge -s test-local
```

In other shell, after kind is started and namespace is created:
```
# alias to use kubectl located in your docker container
alias mlctl='docker exec -it kind-test-local kubectl -n osdk-test'
 
# command that monitors output of ansible running inside of the container
mlctl logs $(mlctl get pods | grep operator | grep Running | awk '{ print $1 }') operator -f
```
