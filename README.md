# Client for CDP
A Python3 client to efficiently perform API requests in the terminal.
# System setup (macOS and Linux)
Clone this repository and add folder to PATH:
```
git clone git@github.com:cognitedata/cdp-cli.git
echo "$(pwd)/cdp-cli" >> ~/.bashrc
```
You can either specify `project` and `apikey` as arguments, or with environment variables
```
export COGNITE_API_KEY=<apikey>
export COGNITE_PROJECT=<project>
```
# Examples
```
cdp-cli --get /assets
```

# Examples with `jq`
`jq` is a lightweight and flexible command-line JSON processor, and is extremely useful to handle JSON responses from our API.
[jq documentation](https://stedolan.github.io/jq/), [tutorial](https://stedolan.github.io/jq/tutorial/) and [download instructions](https://stedolan.github.io/jq/download/).

`cdp-cli --get /assets | jq` (Pretty print)
`cdp-cli --get /assets | jq '.data.items'` (Print .data.items in response)
`cdp-cli --get /assets | jq '.data.items[]'` (Print each element in array)
`cdp-cli --get /assets | jq -c '.data.items[]'` (Print each element, one per line)
`cdp-cli --get /assets | jq -c '.data.items[] | .id'` (Print only id's from all assets)
`cdp-cli --get /assets | jq -c '.data.items[] | {id: .id, name: .name}'` (Create new objects with id's and names)
