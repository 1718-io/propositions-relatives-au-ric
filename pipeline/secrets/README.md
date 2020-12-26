

### Heroku secrets

* For the https://ric-carl.herokuapp.com/ website, the heroku API token

```bash
export SECRETHUB_ORG="ric1718"
export SECRETHUB_REPO="cicd"
secrethub org init -f --name="${SECRETHUB_ORG}" --description="The secrethub org to manage secrets for anything related to https://github.com/1718-io/propositions-relatives-au-ric"
secrethub repo init "${SECRETHUB_ORG}/${SECRETHUB_REPO}"

# --- #
# for the DEV CI CD WorkFlow of
# the ccc website
secrethub mkdir --parents "${SECRETHUB_ORG}/${SECRETHUB_REPO}/carlbot/heroku/"

# --- #
# write quay secrets for the DEV CI CD WorkFlow of
# the Gravitee CI CD Orchestrator
export HEROKU_USERNAME="jean.baptiste.lasselle@gmail.com"
export HEROKU_API_TOKEN="inyourdreams;)"

echo "${HEROKU_USERNAME}" | secrethub write "${SECRETHUB_ORG}/${SECRETHUB_REPO}/carlbot/heroku/user-name"
echo "${HEROKU_API_TOKEN}" | secrethub write "${SECRETHUB_ORG}/${SECRETHUB_REPO}/carlbot/heroku/api-token"

```

### Quay.io (Container images repository)

* For the https://ric-carl.herokuapp.com/ website, the container image definition will be stored at `quay.io/ric1718/une_proposition`

```bash
export SECRETHUB_ORG="ric1718"
export SECRETHUB_REPO="cicd"
secrethub org init -f --name="${SECRETHUB_ORG}" --description="The secrethub org to manage secrets for anything related to https://github.com/1718-io/propositions-relatives-au-ric"
secrethub repo init "${SECRETHUB_ORG}/${SECRETHUB_REPO}"

# --- #
# for the DEV CI CD WorkFlow of
# the ccc website
secrethub mkdir --parents "${SECRETHUB_ORG}/${SECRETHUB_REPO}/carlbot/oci/quay-io/"

# --- #
# write quay secrets for the DEV CI CD WorkFlow of
# the Gravitee CI CD Orchestrator
export QUAY_USERNAME="ric1718+carl"
export QUAY_TOKEN="inyourdreams;)"

echo "${QUAY_USERNAME}" | secrethub write "${SECRETHUB_ORG}/${SECRETHUB_REPO}/carlbot/oci/quay-io/user-name"
echo "${QUAY_TOKEN}" | secrethub write "${SECRETHUB_ORG}/${SECRETHUB_REPO}/carlbot/oci/quay-io/user-pwd"

```
