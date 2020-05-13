
# v1.19

Our goal is to not make radical changes to process or approach, but iterate on our working methods to increase velocity and output in a stable, consistent way.

## 1.19 ii+cncf Team

Many thanks to the contributions of our team:

-   Zach Mandeville ****APISnooper and Tooler****
-   Caleb Woodbine ****Test Writer****
-   Stephen Heywood ****Test Writer****
-   Berno Kleinhans ****Infrastrator+Prowler****
-   Riaan Kleinhans ****Project Manager****

## April News

### prow.cncf.io

Connected to cncf/k8s-conformance!

-   [meow](https://github.com/cncf/k8s-conformance/pull/971)

### SIG-Release 1.19 [Timelines](https://github.com/kubernetes/sig-release/tree/master/releases/release-1.19#timeline) due to Covid

-   Tests need to be in Week 14 (July 16th)
-   Test Freeze Week 16 (July 30th)

### +40 Endpoint Target over 1.19 VS Q2

Conformance Subproject decided to target k8s releases over quarters.

-   +9 in 1.18
-   +40 in 1.19

### -26 Endpoints from Denominator

-   These Endpoints will not be part of Conformance
-   [APISnoop.cncf.io](https://apisnoop.cncf.io) has been updated this +1.77% increase in ‘coverage

### +33 Endpoints Backlogged by Tooling Requests

-   [Watch Tooling](https://github.com/kubernetes/kubernetes/issues/90957) -> +24
    -   Existing PRs +13
        -   \#90944 +2
        -   \#90880 +7
        -   \#90942 +4
    -   Triage +11
        -   \#90877 +6
        -   \#90916 +5
-   [ReplicationController Tooling](https://github.com/kubernetes/kubernetes/issues/90957)
    -   -> +7

### -1 Endpoint from Updated Policy Enforcement

-   New Policy forbids ****kubelet /log api**** usage
-   Two tests lost their ****[Conformance]**** [#90615](https://github.com/kubernetes/kubernetes/pull/90615)
-   Zach did an [Excellent Writeup](https://github.com/cncf/apisnoop/issues/338#issuecomment-627736214)

### Clean Process and Pipelines

-   Conformance Board [ALL](https://github.com/orgs/kubernetes/projects/9) / [ii](https://github.com/orgs/kubernetes/projects/9?card_filter_query=author%3Ariaankl)
-   Riaan now manages the board

## Gate cncf/k8s-conformance PRs

-   [cncf/apisnoop/projects/ cncf/k8s-conformance gate](https://github.com/cncf/apisnoop/projects/29)

### KR1 Setup prow.cncf.io

This repo is outside kubernetes org.

We'll need to set this up in a sustainable/supportable way.

-   [X] DNS prow.cncf.io pointing to prow.apisnoop.io
-   [X] Grant cncf-ci bot permissions to cncf github org
-   [X] Deploy clusters for prow.cncf.io
-   [X] Deploy prow onto said clusters
-   [ ] Researching the isolation / clusters used by test-infra / k8s-infra-wg
-   [ ] Look into setting up #wg-cncf-infra if there is interest

### KR2 Connect cncf/k8s-conformance to prow.cncf.io

Comments and admin actions from prow.cncf.io

Will be made using the [cncf-ci](https://github.com/cncf-ci) bot/github account.

-   [X] Enable [meow](https://github.com/cncf/k8s-conformance/pull/971) and simple prow bot plugins

### KR3 gate+comment w/ list of unrun conformance tests

-   [ ] generate list of test run in a PR
-   [ ] generate list of tests required for PR version
-   [ ] comment with list of missing tests if under 20
-   [ ] comment with count of missing test if over 20
-   [ ] add hold tag if test lists don't match

-   definition

    Influenced by [user stories for KEP-960](https://github.com/kubernetes/enhancements/blob/2c19ec7627e326d1c75306dcaa3d2f14002301fa/keps/sig-architecture/960-conformance-behaviors/README.md#role-cncf-conformance-program)

        Must confirm that the version of the tests being run matches...
        Must confirm the set of tests being run matches...
        Must confirm that all behaviors are covered by a test...

## Gate k/k PRs touching test/e2e or API

-   [k/k API+Conformance Gate](https://github.com/cncf/apisnoop/projects/30)

### Background

Influenced by [Behavior KEP user stories](https://github.com/kubernetes/enhancements/pull/1666/files?short_path=92a9412#diff-92a9412ae55358378bc66295cdbea103) while continuing to focus on endpoints!

> Will show increase in endpoints, and tested endpoints, but also, explicitly, whether conformance coverage increased.

> Comment: "you are adding a new endpoint to stable, and you are adding a conformance test for it"

### OKing PR

> Existing responsiblity via owners file ensures that PRs touching swagger or conformance tests are ****/approved**** by right people.

> A label of ****requires-conformance**** will applied, and ****conformance**** label will need to be added by this gate + automation.

### KR1 Identify a PR as requiring conformance review

PR must touch file in conformance-specific directory

-   (initially /area-conformance + /sig-arch)
-   [ ] Create `run_if_changed` presubmit

    eg: update test/conformance/behaviors/..
    eg: mv from test/e2e to test/conformance

### KR2 Identify list of endpoints added/removed

Tooling will compare `path/operation_id` in `api/openapi-spec/swagger.json`

-   [ ] Generate list of new endpoints
-   [ ] Generate list of removed endpoints

### KR3 Run APISnoop against PR to generate endpoint coverage

Tooling will provide a list of tested and conformant endpoints.

-   [ ] Wait for main prow job to finish
-   [ ] Generate list of hit/tested endpoints
-   [ ] Generate list of conformant endpoints

### KR4 bot comment w/ list of increase/decrease of endpoints

Tooling will comment directly on PR

-   [ ] alpha : endpoints needing tests
-   [ ] beta : endpoints needing tests
-   [ ] stable : comment+block via tag

### KR5 Manual Approval for SIG-Arch (or appropriate owners)

Ensure the API Review process has been followed.

-   [ ] Get feedback on approval process from SIG-Arch
-   [ ] Ensure the correct tagging / OWNERS are respected

### KR6 Donate APISnoop to sig-arch

-   [ ] Get feedback if this is desired
-   [ ] Get as to location of repo under k8s org
-   [ ] Migration maybe in Q3

## Increase Stable Test Coverage by 40 endpoints

### KR1 (5/+40) new conformant stable endpoints

-   5 DONE

    -   +5 Merged [#89753](https://github.com/kubernetes/kubernetes/pull/89753)

-   X IN-PROGRESS

    -   +3 SOAK - Waiting for /approve

### KR2 +9% Coverage Increase 36.46%->45.46%

### KR3 (stretch +49) 50% stable endpoints hit by conformance tests
