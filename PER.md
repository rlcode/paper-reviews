# Prioritized Experience Replay

[`link`](https://arxiv.org/abs/1511.05952)

This paper is about 'Prioritized Experience Replay'

1. PER is Replay memory algorithm to replay important transitions more frequently, and therefore learn more efficiently.
2. Experience reply addresses both of these issues: To break the temporal correlation and rare experience will be used more than single update.
3. The TD-error provides one way to measure these priorities.
4. More TD-error is much 'surprising' or unexpected the trainsition
5. We used the 'sumtree' structure to create a PER.
6. We replayed more samples with larger TD-error.
