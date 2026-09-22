# Evidências — trechos de métodos do AuthService

Arquivo de origem: dominios/srvs/microservice_auth_java/src/main/java/com/miraluh/authservice/auth/AuthService.java

## login (aprox. L86-L96)

```java
@Transactional
public TokenResponse login(LoginRequest request) {
    User user = userRepository.findByEmail(request.email().toLowerCase())
            .orElseThrow(() -> new BadCredentialsException("Invalid credentials"));
    if (user.getPasswordHash() == null
            || !passwordEncoder.matches(request.password(), user.getPasswordHash())) {
        throw new BadCredentialsException("Invalid credentials");
    }
    return issueTokenPair(user);
}
```

## refresh (aprox. L99-L117)

```java
@Transactional(noRollbackFor = InvalidTokenException.class)
public TokenResponse refresh(String rawRefreshToken) {
    RefreshToken stored = refreshTokenRepository.findByTokenHash(sha256(rawRefreshToken))
            .orElseThrow(() -> new InvalidTokenException("Invalid refresh token"));

    if (stored.isRevoked()) {
        int revoked = refreshTokenRepository.revokeAllByUserId(stored.getUser().getId());
        log.warn("Refresh token reuse detected for user {}. Revoked {} active tokens.",
                stored.getUser().getId(), revoked);
        throw new InvalidTokenException("Refresh token reuse detected; all sessions revoked");
    }
    if (stored.isExpired()) {
        throw new InvalidTokenException("Refresh token expired");
    }

    stored.setRevoked(true);
    return issueTokenPair(stored.getUser());
}
```

## logout (aprox. L119-L124)

```java
@Transactional
public void logout(Jwt accessToken) {
    Duration remaining = Duration.between(Instant.now(), accessToken.getExpiresAt());
    blacklistService.blacklist(accessToken.getId(), remaining);
    refreshTokenRepository.revokeAllByUserId(UUID.fromString(accessToken.getSubject()));
}
```

Observação: números de linha aproximados. Consulte o arquivo fonte para referências exatas.
